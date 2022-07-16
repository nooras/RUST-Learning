# RUST-Learning

Day 1:

```
fn main() {
    println!("Hello, world!");
    let x: i32 = 56;
    another_main(1, 2);
    
    //x = 65; // gives error
    // shadwoing
    let x = 62;
    println!("{}", x);
    
    // global scope
    // const constx = 283; // give error
    const constx: i32 = 283;
    
    // scalar - Int, Float, Bool, chars
    // Compund - Tuple, Array
    
    let x: u64 = 5000;
    let x : f32 = 3.14;
    let y: bool = false;
    let y: char = 'c';
    
    // tuple
    let det: ($str, u64) = ("subs", 283);
    println!("{}", det.0);
    
    // array
    let arr = [1,2,3,4];
    println!("{}", arr[0]);
    
}

//Void
fn another_main(x: i32, y:i32) {
    // statements
    println!("{}", x);
    println!("{}", y);
    
    // expression
    let mul = x * y;
    println!("{}", mul);
}

// return
fn another_main(x: i32, y:i32) -> i32 {
    let mul = x * y;
    //return mul; // OR mul withour semicolon
    mul
}

// conditional if else
fn conditional_main(x: i32) -> bool {
    if x < 5 {
       return true ;
    } else x == 5 {
        return true ;
    } else {
        return false;
    }
}

// one line conditional
fn onelineConditional(x: bool){
    // let res = if x {"correct"} else {404}; // cannot return 2 DT
    let res = if x {"correct"} else {"404"};
}

// loops
fn loops(){
    /*
    loop
    whiel loop
    for in loop
    */
    loop {
        println!("hii"); 
        break; // break the loop
    }
    
    // loop
    let mut counter = 0;
    loop {
        counter += 1;
        println!("{}", counter);
        if counter == 10 {
            break;
        }
    }
    // storing value & break the loop
    counter = 0;
    let res = loop {
        counter += 1;
        println!("{}", counter);
        if counter == 10 {
            break counter *2; // returns the value after break
        }
    }
    
    // while
    while counter != 0{
        println!("{}", counter);
        counter -= 1;
    }
    
    // for in
    let arr = [1,2,3,4,5,6];
    for element in arr {
        println!("{}", element);
    }
    for element in arr.iter() {  // using iter
        println!("{}", element);
    }
    for element in (1..4).rev { // excluding 4 value -range 1 -3
        println!("{}", element);
    }
    for element in (1..=4).rev { // including 4 as well 1 - 4
        println!("{}", element);
    }
}
```
Day 2:

```
fn main() {
    // some points
    // functions don't support mutability concept.
    // Self means the type itself.
    // impl is for methods..it means implement
    // Derive is the shortcut
    // new is just a name of the function.
    // Constructor basically means instantiating a type That's why it is named as new.
    // IpAddrKing is just a type like String.
    
    println!("Hello, world!");
    let x = Person::new("nooras", 12);
    x.age_up(12);
    
    let z = get_age(&x);
    x.age_up(12); // cannot access
    // method - ::, associated funtion - .
    let somevalue = IpAddsKind::V4;
    let somkind = match somevalue {
        IpAddsKind::V4 => println!("This is version 4"),
        IpAddsKind::V5 => println!("This is version 55")
    }
    println!("{:?}", somkind)
    let optVelue: Option<i32> = Some(10);
    println("{:?}", optVelue);
    let optVelue: Option<i32> = None;
    println("{:?}", optVelue);
    let okerror: Result<i32, i32> = Ok(1);
    println("{:?}", okerror);
}

#[derive(Debug)]
enum IpAddsKind{
    V4(u8, u8, u8, u8), 
    V6(u37)
}

// used when option is opotional
// rust doesnt support null 
enum Option<T>{
    Some<T>,
    None
}

enum Result<T, E>{
    Ok<T>,
    Err<E>
}

// public
pub struct Person{
    name: "String",
    age: i32
}

impl Person{
    pub fn new(name:Strng, age:i32) -> self{
        Person{name, age:x}
    }
    // method - having self keyword is method
    pub fn greet(&self) -> String {
        format!("Hi my name is {}". self.name);
    }
    // associated funtions  - taking some values
    pub fn add(x:i32, y:i32) -> i32{
        
    }
    pub fn age_up(&mut self, n:i32){
        self.age += n;
    }
    // self, &self, mut self
    // &self - read
    // mut selft - fold mutable ref - consume the onwership
}
pub fn get_age(s: &Person) -> i32{
    &s.age
}

fn ownerships(){
    let s = "hello";
    { //closures - anonymous funtion
        let s1 = "bye"; //str stack - str literal- immutable
        let s1 = "bye".to_string(); //string heap - string - mutable
    }
    println!("{}", s1);
    
    // string slices
    let x = String::from("Hello");
    let y = &x[1..]; // slicing from index 1 - ello
    
    // rules
    let x = 1;
    let z = &x; // only one muatble referce
    let a = &mut x; // can access onl
    *a = 2; // need to dereference
    
    let v = vec![1,2,1,3,5]; // dynamic - heap stores
    for i in v.iter(){
        if *i == 1{
            println!("one")
        }
    }
    
    let mut vectorrr = Vec::new();
    vectorrr.push(1);
    println!("{:?}", vectorrr);
    println!("{} {}", vectorrr.len(), vectorrr.capacity()); //default capacity of vector(size) is 4 

}


fn structs_enum(){
    // customs type need to inmplemte using therad
    // structs & // enum
    // structs - attributes - primitive type
    
    //Derive is an easier way to implement traits for a specific. - Hence Debug is a trait
    #[derive(debug)]
    struct User {
        // attributes having primtive dt
        active::bool,
        username::String,
        email::String
    }
    // enum - hold differnt types - custom types
    
    // constructor
    //impl means adding functionality to that type. Can have n number of funtions. iplementation for trsucts
    impl User {
        // design pattern - adapter, factory - TODO
        // -> fish symbol
        // self - first insatnce
        fn new(active: bool, username:String, email:String) -> Self{
             User { active: false, username: "nooras".to_string(), email: "nooras@gmail.com".to_string()}
        } 
    }
    
    let x = User { active: false, username: "nooras".to_string(), email: "nooras@gmail.com".to_string()};
    
    let x = User::new(fasle, "a".to_string(), "b".to_string);
    
    println!("User: {:?}", x)

}
```
