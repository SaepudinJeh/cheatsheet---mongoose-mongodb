#### Contains a collection of previously worked on Mongoose/MongoDB cheat sheets

---
> Example Update object in array
```Javascript
  const updatePaypal = await this.methodPaymentModel.findOneAndUpdate(
      { account, 
          $or: [
              { 'paypal.paypalNumber': data.paypalNumber },
              { 'paypal.email': data.email },
          ] 
      },
      { $set: { 'paypal.$[]': data } },
      { new: true }
  )
````
