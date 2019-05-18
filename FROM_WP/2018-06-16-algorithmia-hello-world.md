# Algorithmia Hello World

Here is the [Getting Started](https://algorithmia.com/developers/getting-started) page for Algorithmia.

## CURL

If you’re logged in when you visit the page, they’ll fill in your credentials for your first cURL command, so you can copy and paste it into the console to get it working!

This was my result: (*** for blocking my username)

```
{“result”:”Hello j********”,”metadata”:{“content_type”:”text”,”duration”:0.000589006}}
```

Woohoo!

## Client Code

And they also have client code for this too!

Tip: I had to run [‘pip install algorithmia‘](https://pypi.org/project/algorithmia/) for this to work because I didn’t have the Algorithmia package installed in my environment, so the import wasn’t working.

```
import Algorithmia

input = “jonathans232”
client = Algorithmia.client(‘*******************************’)
algo = client.algo(‘demo/Hello/’)
print( algo.pipe(input).result ) # I’m using Python 3 so my syntax is adjusted
```

(I’m using Python, but they also have Python, Java, R, Go, etc)

## Nearly Real Life Example

Ok, just one more example!

I’ll use the [Seniment Analyzer](https://algorithmia.com/algorithms/nlp/SentimentAnalysis) API at ‘nlp/SentimentAnalysis/1.0.4’.

I just added the following code to a copied file of the preceding code:

```
algo2 = client.algo(‘nlp/SentimentAnalysis/1.0.4’)
document = “Jonathan is a bad machine learning engineer”
print( algo2.pipe(document).result )
```

I got results of 1, 2, or 3 for different statements:

- 1 = “Jonathan is a bad machine learning engineer”
- 2 = “Jonathan is a okay machine learning engineer”
- 3 = “Jonathan is a great machine learning engineer”

## Conclusion

Algorithmia has some very exciting features and I’m excited to use them to develop software. Feel free to learn more about them!
