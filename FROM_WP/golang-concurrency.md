# Golang Concurrency Example: Scatter-Gather

Hello, I just want to throw this out there for those who are first learning about concurrency or parallelism.This post was inspired by Peter Bourgen and this post is basically a concretization of a [pseudo-code sample](https://peter.bourgon.org/go-for-industrial-programming/#scatter-gather) that he put in one of his great tech articles.Back to those who are new to Golang's concurrency model; First, here's a quote from Rob Pike : "[Concurrency is not Parallelism](https://www.youtube.com/watch?v=cN_DpYBzKso&t=1174s" and I would summarize in my own words that: Concurrency is not parallelism, but it can be used to create parallelism. And that's really getting to the heart of this specific code sample. If that's enough explanation to you and you want to get to the code, skip the following paragraphs.Long explanation: Generally, they are similar in mechanics, but different in purposes.Concurrency is generally about handling a 1000 different things at the same time. An example of this is a server who has 4 different endpoints, at which they receive HTTP request, and then send back HTTP responses. A Server like that should be able to handle many many many requests at the same time.Parallelism, or parallel computing, is specifically meant to speed up gargantuan computations. It is the method of breaking down a HUGE computation (or math problem) into smaller pieces, and then letting multiple computers and/or multiple computing cores in a computer work on pieces of the computation all at the same time, and then summing up or combining the result of the broken down computations into a final computation. An example of this in Machine Learning is the application of [MapReduce](https://www.ibm.com/analytics/hadoop/mapreduce), the idea behind [Hadoop](https://hadoop.apache.org/). Without further ado, here is the code sample:

## This is what you would you would copy-paste into a gomacro [interactive golang console](https://github.com/cosmos72/gomacro#installation):
import "fmt"type result struct {
    Val float64
    Err error
}func process() (float64, error) {
    return 5.0, nil
}c := make(chan result, 10)
var totalfloat float64// Scatter
for i:= 0; i < cap(c); i++ {
    go func() {
        val, err := process()
        c <- result{val, err}
    }()
}// Gather
for i := 0; i < cap(c); i++ {
    res := <-c
    if res.Err == nil {
        totalfloat += res.Val
    }
}fmt.Println("totalfloat: ", totalfloat)
// totalfloat:  50

## This is what you would put into a file and then run with "go run scatter-gather.go" (assuming you named the file 'scatter-gather.go')package main

import "fmt"

type result struct {
Val float64
Err error
}

func process() (float64, error) {
return 5.0, nil
}

func main() {

c := make(chan result, 10)
var totalfloat float64
// Scatter
for i := 0; i < cap(c); i++ {
go func() {
val, err := process()
c <- result{val, err}
}()
}
// Gather
for i := 0; i < cap(c); i++ {
res := <-c
if res.Err == nil {
totalfloat += res.Val
}
}
fmt.Println("totalfloat: ", totalfloat)
}


=====================

Golang Concurrency Example: Scatter-Gather
Posted on November 14, 2018 by Jonathan Steele
Hello, I just want to throw this out there for those who are first learning about concurrency or parallelism.

This post was inspired by Peter Bourgen and this post is basically a concretization of a pseudo-code sample that he put in one of his great tech articles.

Back to those who are new to Golang’s concurrency model; First, here’s a quote from Rob Pike : “Concurrency is not Parallelism” and I would summarize in my own words that: Concurrency is not parallelism, but it can be used to create parallelism. And that’s really getting to the heart of this specific code sample. If that’s enough explanation to you and you want to get to the code, skip the following paragraphs.

Long explanation: Generally, they are similar in mechanics, but different in purposes.

Concurrency is generally about handling a 1000 different things at the same time. An example of this is a server who has 4 different endpoints, at which they receive HTTP request, and then send back HTTP responses. A Server like that should be able to handle many many many requests at the same time.

Parallelism, or parallel computing, is specifically meant to speed up gargantuan computations. It is the method of breaking down a HUGE computation (or math problem) into smaller pieces, and then letting multiple computers and/or multiple computing cores in a computer work on pieces of the computation all at the same time, and then summing up or combining the result of the broken down computations into a final computation. An example of this in Machine Learning is the application of MapReduce, the idea behind Hadoop.

Without further ado, here is the code sample:

This is what you would you would copy-paste into a gomacro interactive golang console:

import "fmt"
type result struct {
    Val float64
    Err error
}
func process() (float64, error) {
    return 5.0, nil
}
c := make(chan result, 10)
var totalfloat float64
// Scatter
for i:= 0; i < cap(c); i++ {
    go func() {
        val, err := process()
        c <- result{val, err}
    }()
}
// Gather
for i := 0; i < cap(c); i++ {
    res := <-c
    if res.Err == nil {
        totalfloat += res.Val
    }
}
fmt.Println("totalfloat: ", totalfloat)
// totalfloat:  50
This is what you would put into a file and then run with “go run scatter-gather.go” (assuming you named the file ‘scatter-gather.go’)
package main

import "fmt"

type result struct {
Val float64
Err error
}

func process() (float64, error) {
return 5.0, nil
}

func main() {

c := make(chan result, 10)
var totalfloat float64
// Scatter
for i := 0; i < cap(c); i++ {
go func() {
val, err := process()
c <- result{val, err}
}()
}
// Gather
for i := 0; i < cap(c); i++ {
res := <-c
if res.Err == nil {
totalfloat += res.Val
}
}
fmt.Println("totalfloat: ", totalfloat)
}