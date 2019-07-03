...
async goto_anim (dest) {
  var acceleration = 0.2;
  var temp_lat = this.center.lat;
  var temp_long = this.center.lng;
  var temp_counter = 0;
  while (temp_counter < 100){
    temp_lat = (dest.lat-temp_lat)*acceleration*acceleration + temp_lat;
    temp_long = (dest.lng-temp_long)*acceleration*acceleration + temp_long;
    this.center = L.latLng(temp_lat, temp_long);
    await this.sleep(5);
    temp_counter += 1;
  }
},
sleep(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}
...
