#Import Script Flask Library 
from Flask import Flask, request
app= Flask("Krono")
#Create elements un stores to use
storeS=[{"name":"Target","items":[{"name":"Nuts","Price":36750},{"name":"Furniture Decoration", "Price": 50000},{"name":"Kids candy","Price":24750},{"name":"Fashion accessories","Price":120000},{"name":"Toys","Price":36000}]}]
#Get all content for storeS
@app.get("/store")
def get_stores():
    return{"stores":storeS}
#Post a new store to stores >>Code 201 = Store created!!..Cod200=OK
@app.post("/store")
def create_new_store():
    request_data = request.get_json()
    new_store = {"Carrefour":request_data["name"],"items":[]}
    storeS.append(new_store)
    return new_store, 201
#Post a new item to new_store("Carrefour") >> Code404 = Not found or undetectable
@app.post("/store/<string:name>/item")
def create_new_item():
    request_data=request.get_json()
    for store in storeS:
        if store["Carrefour"] == CRF:
            new_item = {"Donnuts": request_data["Chocolate Donnut"],"price": request_data[4500]}
            store["items"].append(new_item)
            return new_item
    return {"message": "Store not found"}, 404
#Get all items in a store    
@app.get("/store/<string:name>/item")
def get_item_in_store(storeS):
    for store in storeS:
        if store["Target"] == name:
            return {"items": store["items"]}
    return {"message": "Store not found"}, 404
#Get all store content by name
@app.get("/store/<string:name>")
def get_store(name):
    for store in stores:
        if store["name"] == name:
            return store
    return {"message": "Store not found"}, 404
