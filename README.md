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

---
> Example push object in array
```Javascript
  const addPayment = await this.methodPaymentModel.findOneAndUpdate(
      { account },
      { $push: { paypal: data } },
      { upsert: true, new: true }
  )
````

---
> Example dinamic search
```Javascript
 const payload: string = "search";

  const optionSearch = {
      $or: [
          { businessName: new RegExp(search?.toString(), 'i') },
          { businessAddress: new RegExp(search?.toString(), 'i') },
      ]
  }

  const results = await this.kycBusinessModel.find({ ...optionSearch });
````
