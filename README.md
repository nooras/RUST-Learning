# RUST-Learning

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
