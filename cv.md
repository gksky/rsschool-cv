# Alexander Gutkovsky

## Contact Info: 
* City: Minsk
* E-mail: a.gutkovsky@gmail.com
* Mobile: +375 (29) 611-71-33

## Summary
I want to learn JavaScript to make money by developing front-end and back-end applications.

## Skills
Basic skills in HTML, CSS, JS (Node, Vue, Nuxt, Vuetify), PHP, C, MySQL.

## Code examples
```javascript
pool.query("UPDATE ttnregistry SET `dt`='" + req.body.date + "', `from`='" + req.body.from.unp + "', `to`='" + req.body.to.unp + "', `fromID`='" + req.body.from.id + "', `toID`='" + req.body.to.id + "', `orderUNP`='" + req.body.order + "', `contract`='" + req.body.contract + "', `load`='" + req.body.load + "', `unload`='" + req.body.unload + "', `truck`='" + req.body.truck + "', `trailer`='" + req.body.trailer + "', `driver`='" + req.body.driver + "', `waylist`='" + req.body.waylist + "', `allowed`='" + req.body.allowed + "', `handover`='" + req.body.handover + "', `fromname`='" + req.body.from.name + "', `toname`='" + req.body.to.name + "' WHERE id=" + findid[0].id, function(err, data) {
  if(err) return console.log(err);
  pool.query("DELETE FROM ttnequipment WHERE `ttnID`=" + findid[0].id, function(err, data) {
    if(err) return console.log(err);
      res.json(data);
    });
    var eqjson = '';
    req.body.equipment.forEach((item, i) => {
      delete req.body.equipment[i].workheight; delete req.body.equipment[i].price; delete req.body.equipment[i].minrent; delete req.body.equipment[i].tenantID; delete req.body.equipment[i].location; delete req.body.equipment[i].rentprice;
      pool.query("INSERT INTO ttnequipment (`ttnID`, `equipmentID`, `quantity`, `cost`) VALUES ('" + findid[0].id + "', '" + req.body.equipment[i].id + "', '" + req.body.equipment[i].quantity + "', '" + req.body.equipment[i].cost + "')", function(err, data) {
        if(err) return console.log(err);
      });
      eqjson = eqjson + JSON.stringify(req.body.equipment[i]) + ',';
      pool.query("UPDATE equipment SET `tenantID`='" + req.body.to.id + "', `location`='" + req.body.unload + "' WHERE `id`='" + req.body.equipment[i].id + "'", function(err, data) {
        if(err) return console.log(err);
      });
    });
  eqjson = eqjson.slice(0, eqjson.length-1)
  pool.query("UPDATE ttnregistry SET equipment='[" + eqjson + "]' WHERE `id`=" + findid[0].id, function(err, data) {
    if(err) return console.log(err);
  });
});
```
```javascript
setTenantByUNP(unp) {
  var index = this.toList.findIndex(n => n.unp === unp);
  if (index !== -1) {
    this.tenant = this.toList[index];
    this.$axios.get('/contract?company=' + this.landlord.id + '&' + 'partner=' + this.tenant.unp).then(res => {
      this.contractList = res.data;
      for (let i = 0; i < this.contractList.length; i++) {
        if (this.contractList[i].typeofcon === 0) {
          this.contractList[i].fullname = this.contractList[i].name.toLowerCase().replace(/договор/i, 'Договору') + ' №' + this.contractList[i].number + ' от ' + this.contractList[i].dateofcon.substr(0, 10).split('-').reverse().join('.');
        } else {
          this.contractList.splice(i, 1);
          i--;
        }
      }
    })
  }
}
```
