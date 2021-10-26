# javaScriptStudies
Estudo de Java Script  pelo curso Plural Sight e Object, Prototyes e Classes

Para juntar dois Objects ou copiar os dados de um para outro objeto:

```JavaScript 
 let person = {
        firstName: "Jim",
        lastName: "Cooper",
        age: 21,
        isAdult() { return this.age >= 18; } // esse tipo de funcao só funciona dentro de Objetos 
 }
 
  let healthStats = {
        status: "Working",
        height: 1,75
  }

Objects.assign(person1, healthStats); 
// return Objects.assign({},person, healthStats); DESSA FORMA CRIA UM NOVO OBJETO E NAO ALTERA OUTROS(person)

display(person1); // vai mostrar ambos person e healthStats em em person
```
## Properties

Para editar como se mostra a propriedade de um objects é necessário  apenas usar:

```JavaScript 
for (let propertyName in person){
    display( propertyName + ': '+ person[propertyName]);
}
```
Agora sobre editar os valores de uma property pode se setar como (false or true):
- **writable (se o valor pode ser alterado ou não)

Usando:
`Object.defineProperty(person, 'firstName', {writable: false});`

- **enumerable (tira a numeração da property, só sera posivel ver com `display(person.firstName)`

Usando:
`Object.defineProperty(person, 'firstName', {enumerable: false});`

- **configurable (bloqueia para configuração de property, apenas writable, e tambem nao deixa deletar com `delete person.firstName;`)

Usando:
`Object.defineProperty(person, 'firstName', {configurable: false});`

### Creating Property GET and SET

Get show and Set edit:

```JavaScript 
let person = {
  name:{
    first: 'Jim',
    last: 'Cooper'
  }
}

Objects.defineProperty(person, 'fullName',
{
  get: function() {
    return this.name.first + ' ' + this.name.last;
  }
  set: function(value) {
    var nameParts = values.split(' ');
    this.name.first = nameParts[0];
    this.name.last = nameParts[1];
  }
}

person.fullName = 'Fred Jones'; // isso muda o nome completo e o firts and last no objeto acima

```
### Prototypes and Inheritance(Heranca)

Prototype é um objeto que esta em todas as funções  de JavaScript. É usado como um protótipo  quando a função  é usado como um contrutor de objectos. Quando se muda um prototype todos objetos que usam essa Function Prototype iram mudar também `Person.prototype.age = 30 todos objetos teram 30 anos.
Porém se editar apenas diretamente o `jim.age = 18` pela Inheritance apenas o jim tera 18, e tambem tera agora sua propria property AGE.

Em um cadeia/corrente de Inheritance é necessário criar 3 linhas:
Dentro da função: `Person.call(this, firstNAme, lastName, age)`// para trazer as infos de Person para Student
Fora da função : `Students.prototype = Objects.create(Person.prototype);`
                 `Students.prototype.constructor = Student;`

## Classes:
A classe é similar a uma Function Contructer, sua estrutura é dada como:

```JavaScript 
class Person{
  contructor(firstName, lastName, age){
   this.firstName = firstName;
   this.lastName = lastName;
   this.age = age;
  }
}
let jimPerson = new Person('Jim', 'Cooper', 29); // cria um objeto apartir da class
```

### Creating GET and SET in CLASS

```JavaScript 
class Person{
  contructor(firstName, lastName, age){
   this.firstName = firstName;
   this.lastName = lastName;
   this.age = age;
  }
  get fullName {
    return this.name.first + ' ' + this.name.last;
  }
  set fullName {
    var nameParts = values.split(' ');
    this.name.first = nameParts[0];
    this.name.last = nameParts[1];
  }
}
```
### Add Functions in CLASS

```JavaScript 
class Person{
  contructor(firstName, lastName, age){
   this.firstName = firstName;
   this.lastName = lastName;
   this.age = age;
  }
  isAdult(){
  returno this.age >= 18;
  }
}
```
### Propertype in CLASS

Sim existe propertype em classes assim como nas funções  e são  definidas  de uma forma similar:
Usando:
`Object.defineProperty(Person.proportype, 'firstName', {enumerable: true});` // usado da mesma forma com outros Proportype

### Inheritance(Heranca) in CLASS 

 Para realizar as herancas nas CLASS é necessário  apenas EXTENDS;
 ```JavaScript 
 class Students extends Person {
  contructor(firstName, lastName, age){
   super(firstName, lastName, age);
   this.enrolledCourses = [];
  }
  enroll(curseId) {
   this.enrolledCouses.push(courseId);
  }
  getCourses(){
   return this.fullName + " está cursando:" + this.enrolledCouses.join(", ");
 } 
```

