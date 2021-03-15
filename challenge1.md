const mongoose = require("mongoose");
const express = require("express");
const router = express.Router();
const app = express();

const SleepSchema = new mongoose.Schema({
    struggglingDays: { type: String, enum: ["Less than 2 weeks", "2 to 8 weeks", "More than 8 weeks"] },
    bedTime:Number,
    bedOutTime:Number,
    sleepingHour:Number,
    });

const Sleep = mongoose.model("Sleep", SleepSchema);

router.post("/", adminAuth, async (req, res) => {
  let sleep = new Sleep({
    struggglingDays:req.body.struggglingDays,
    bedTime:req.body.bedTime,
    bedOutTime:req.body.bedOutTime,
    sleepingHour:req.body.sleepingHour,
  });
  await sleep.save();
  return res.send({ message: "Success", data: "data added successfully" });
});

app.use(express.json());
app.use("/api/admins", router);

mongoose.connect(db).then(() => winston.info(`Connected to ${db}...`));
const port = process.env.PORT || 3000;
const server = app.listen(port, () => console.log(`Listening on port ${port}...`));
