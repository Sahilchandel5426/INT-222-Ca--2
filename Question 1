const path = require("path");
const express = require("express");
const app = express();
const mongoose = require('mongoose');
const bodyparser = require('body-parser');
var urlencodedParser = bodyparser.urlencoded({ extended: false })

main().catch(err => console.log(err));

async function main() {
    await mongoose.connect('mongodb://localhost:27017/valorantTour');
}


var valoSchema = new mongoose.Schema({
    name: {
        type: String,
        required: true
    }, 
    valo_id:{
        type: String,
        required: true
    },
    mobile_number: {
        type: String,
        required: true
    }
})
var valorant = mongoose.model('valorant', valoSchema);



// console.log(__dirname , "./public");
const staticPath = path.join(__dirname, "./public")

app.use(express.static(staticPath));

//   
app.set('trust proxy', true)

// app.use(express.json());

app.get('/', (req, res) => {
    res.send('hellow')
});

app.post('/', urlencodedParser, (req, res) => {
    console.log(req.body)
    var myData = new valorant({
        name: req.body.FName,
        valo_id: req.body.VID,
        mobile_number:req.body.MNo

    })
    myData.save().then(() => {
        res.send("this item has been saved to database")
    }).catch(() => {
        res.status(400).send("Item was not saved to database")
    })


})

app.listen(3000, () => {
    console.log('listening')
})
