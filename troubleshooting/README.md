# Files for troubleshooting the floorplan card not showing objects that have a "set clip".

The yaml file as is references `tesla_floorplan_v1.svg`. This doesn't work. 

If I take all the "clipped" objects and make "bitmap copy", it doers work (to test this, change part of line 4 in the yaml file from `tesla_floorplan_no_clip.svg` to `tesla_floorplan_no_clip.svg`)
