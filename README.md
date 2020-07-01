const builtMustang = {
        _version: { 
        model: [], 
        bodyModel: [], 
        color: [],
        engine: [],
    },
    get model() {
      return this._version.model;
    },
    get bodyModel() {
      return this._version.bodyModel;
    },
    get color() {
      return this._version.color;
    },
    get engine() {
      return this._version.engine;
    },
    set model (model) {
      this._version.model = model;
    },
    set bodyModel (bodyModel) {
      this._version.bodyModel = bodyModel;
    },
    set color (color) {
      this._version.color = color;
    },
    set engine (engine) {
      this._version.engine = engine;
    },

    get version () {
      return {
model: this.model,
bodyModel: this.bodyModel,
color: this.color,
engine: this.engine,
      };
    },
addModelsToMustang (optionName, modelName, modelPrice) {
  const mustang ={
name: modelName,
price: modelPrice,
  };
  return this._version[optionName].push(mustang);
},
getRandomMustangFromVersion(optionName) {
  const versions = this._version[optionName];
  const randomIndex = Math.floor(Math.random() * versions.length);
  return versions[randomIndex];
},
generateRandomMustang() {
  const models = this.getRandomMustangFromVersion('model');
  const bodyModels = this.getRandomMustangFromVersion('bodyModel');
  const colors = this.getRandomMustangFromVersion('color');
  const engines = this.getRandomMustangFromVersion('engine');
  const totalPrice = models.price + bodyModels.price + colors.price + engines.price;
  return `Your all new Mustang is a ${models.name} ${bodyModels.name}, with a ${colors.name} color and the ${engines.name} as a heart. Your total price it will be ${totalPrice}.`;
}
};

builtMustang.addModelsToMustang('model', 'GT', 28000.00);
builtMustang.addModelsToMustang('model', 'Mach5', 34000.00);
builtMustang.addModelsToMustang('model', 'Cobra', 63000.00);

builtMustang.addModelsToMustang('bodyModel', 'fastback', 1000.00);
builtMustang.addModelsToMustang('bodyModel', 'convertible', 3000.00);

builtMustang.addModelsToMustang('color', 'Racing Blue', 500.00);
builtMustang.addModelsToMustang('color', 'Dark Knight', 300.00);
builtMustang.addModelsToMustang('color', 'Blood Red', 100.00);

builtMustang.addModelsToMustang('engine', 'V6', 1000.00);
builtMustang.addModelsToMustang('engine', 'V8', 3000.00);
builtMustang.addModelsToMustang('engine', 'V8Biturbo', 8000.00);

const newMustang = builtMustang.generateRandomMustang();
console.log(newMustang);
