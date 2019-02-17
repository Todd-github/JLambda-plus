# JLambda-plus
POJM, FAAR

In [Cloud Programming Simplified: A Berkeley View on Serverless Computing](https://arxiv.org/abs/1902.03383v1), the author lists serveral obstacles for serverless computing. And this project aims to overcome some of them.

1. POJM: Plain Ordinary Java Method, Function as a Resource. A functional service is a function, and it should be a plain method. It should be limited to a part of an interface or something else. In JLambda-plus, any method annotated with @Macro and @Path can be published as a functional service. Most of the jobs will be done by framework automically. A function can be multi-written using different language, and they need not to share a SDK or anything else. The only thing to guarantee is the parameter and return object should be consistent documented by a json or protobuf file. Some fuction should be deployed in particular machines, while others needn't as long as there is language runtime there.
2. Solution as a Graph. A graph should be described in normal language, like java in this project, and plain grammer. Plain grammer means you need not use tensorFlow like syntax:
```
Node n1 = tf.aFunction(...);
Node n2 = tf.aFunction(...);
Node n3 = tf.aBiFunction(n1, n2);
```
That's tedious for so many *tf*, plain grammer should like this:
 ```
XXX n1 = aFunction(...);
XXX n2 = aFunction(...);
XXX n3 = aBiFunction(n1, n2);
```
Not only no *tf*, but also n_ has a class declaration XXX.

3. FAAR: Function as a Resource. Every function called in the graphing processure will be allocated a URI according its method signature, class name, etc. A URI means you can locate it and trace every single function call in this solution and alter them if needed.

4. Ship the code to data. Some functions in the solution are data related and there would be a large transport cost if they are deployed apart. We call immovable function as anchor function, mostly because they hold big data. Other fuction that handle these datas should be shipped there and run in the same process with the anchor function.
