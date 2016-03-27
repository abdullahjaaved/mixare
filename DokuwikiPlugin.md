#chris made a plugin for exporting docuwiki content to mixare!

See the original post at:
http://groups.google.com/group/mixare-development/browse_thread/thread/48598002d8225b10/2f1729ad70526225

Thanks Chris for this awesome contribution, his original mail follows:


Hi,

i made a feed-processor for the great dokuwiki-plattform.

dokuwiki is a free, secure, oss wiki running without a database on a
php-server.

http://www.dokuwiki.org/dokuwiki

to add a location to your article you will need a plugin called
"geotag"
http://www.dokuwiki.org/plugin:geotag

for easy generation of tags you can use
http://t2mo.cc/services/geotag/
(click on the map to get a position)

to grab all articles within your radius you will need this
```
<?php

if(!defined('DOKU_INC')) define('DOKU_INC', dirname(__FILE__).'/');
require_once(DOKU_INC.'inc/init.php');

//ini_set('display_errors', 1);

$base_url = 'http://'.dirname($_SERVER['SERVER_NAME'].$_SERVER['REQUEST_URI']).'/doku.php?id=';


//  $l1 ==> latitude1
//  $o1 ==> longitude1
//  $l2 ==> latitude2
//  $o2 ==> longitude2 
function haversine($l1, $o1, $l2, $o2) {
    $l1 = deg2rad ($l1);
    $sinl1 = sin ($l1);
    $l2 = deg2rad ($l2);
    $o1 = deg2rad ($o1);
    $o2 = deg2rad ($o2);
                
    return (7926 - 26 * $sinl1) * asin (min (1, 0.707106781186548 * sqrt ((1 - (sin ($l2) * $sinl1) - cos ($l1) * cos ($l2) * cos ($o2 - $o1)))));
}  



// getBoundingBox
// hacked out by ben brown <ben@xoxco.com>
// http://xoxco.com/clickable/php-getboundingbox

// given a latitude and longitude in degrees (40.123123,-72.234234) and a distance
// calculates a bounding box with corners $distance away from the point specified.
// returns $min_lat,$max_lat,$min_lon,$max_lon 
function getBoundingBox($lat_degrees, $lon_degrees, $distance) {

	//$radius = 3963.1; // of earth in miles
	$radius = 6371; // of earth in km
	
	// bearings	
	$due_north = 0;
	$due_south = 180;
	$due_east = 90;
	$due_west = 270;

	// convert latitude and longitude into radians 
	$lat_r = deg2rad($lat_degrees);
	$lon_r = deg2rad($lon_degrees);
		
	// find the north, south, east and west corners $distance away
	// original formula from http://www.movable-type.co.uk/scripts/latlong.html
	$north  = asin(sin($lat_r) * cos($distance/$radius) + cos($lat_r) * sin ($distance/$radius) * cos($due_north));
	$south  = asin(sin($lat_r) * cos($distance/$radius) + cos($lat_r) * sin ($distance/$radius) * cos($due_south));
	
	$east = $lon_r + atan2(sin($due_east)*sin($distance/$radius)*cos($lat_r),cos($distance/$radius)-sin($lat_r)*sin($lat_r));
	$west = $lon_r + atan2(sin($due_west)*sin($distance/$radius)*cos($lat_r),cos($distance/$radius)-sin($lat_r)*sin($lat_r));
	
	$north = rad2deg($north);
	$south = rad2deg($south);
	$east = rad2deg($east);
	$west = rad2deg($west);
	
	// sort the lat and long so that we can use them for a between query	
	$llat = array($south,$north);
	sort($llat);
	$llon = array($west,$east);
	sort($llon);
	return array_merge($llat, $llon);
}


$lat = floatval($_GET['latitude']);
$lon = floatval($_GET['longitude']);
$radius = floatval($_GET['radius']);


if( $lat!=0 && $lon!=0 && $radius>0 ) {
	
	// get the Bounding-Box for your search
	$ll = getBoundingBox($lat,$lon,$radius);
	
	// take the given altitude for all POIs
	$alt = intval($_GET['altitude']);
	
	// define the JSON-Array
	$json = array();
	
	// superquick Way to get all Wiki-Pages
	$pages = glob('data/pages/*.txt');
	$i = 0;
	// check all Pages
	foreach($pages as $page) {
		
		$name = substr(array_pop(explode('/',$page)),0,-4);
		
		// check for Geo-Tags
		if($arr = p_get_metadata($name, 'geo', true)){
			
			// Position within 
			if(	$arr['lat']>$ll[0] && $arr['lat']<$ll[1] && 
				$arr['lon']>$ll[2] && $arr['lon']<$ll[3] 
			){
				$nlat = floatval($arr['lat']);
				$nlon = floatval($arr['lon']);
				$json[] = array(
					'id' => $i,
					'title' => $name,
					'lat' => $nlat,
					'lng' => $nlon,
					'elevation' => $alt,
					'distance' => haversine($lat,$lon,$nlat,$nlon) * 1000,
					'has_detail_page' => '1',
					'webpage' => urlencode($base_url.$name)
				);
				$i++;
			}
		}
	}
	$out = array('status'=>'OK', 'num_results'=>$i, 'results'=>$json);
	echo json_encode($out);
	
}

?>
```
put this script in the main folder and call it via mixare.