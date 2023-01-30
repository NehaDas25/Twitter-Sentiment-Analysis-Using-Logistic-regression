# Work Report

## Information

- Name: DAS, NEHA
- CIN: 401457144
- GitHub: NehaDas25
- Email: ndas@calstatela.edu

## Features

- Not Implemented:
  - PART-5: ERROR ANALYSIS
    - As provided in the assignment notebook, that some tweets our model misclassified.
    - Clearly see that processed tweet doesn't process as per the expectations of the tweet provided.
    - Which results in making a positive tweet classify as negative tweet.
    - On opinion, need may be a vectorization technique to be applied?
    - Feeding the train_x and test_y with higher number of iterations and using multiple deep learning algorithms could help achieve this goal for error parsing.
  
  - PART-6: PREDICT OWN TWEET.
    - Took a latest twitter from @ElonMusk: "Another major improvement in timeline refresh speed just released – now 10X faster than a few months ago". Its a good improvement which is referred as 10 times faster than it was few weeks ago.
    - In my opinion, should have been classified as Positive Tweet, but was classified a Negative Sentiment.

<br><br>

- Implemented: In the assignment, to achieve the end goal, all parts are implemented sequentially.

  - PART-1: LOGISTIC REGRESSION
   - PART-1.1: Implemented Sigmoid Function _h(z)_ using the formulae as provided. It works for both scalar values and array of values. This passed all the unit-test cases as well.
   - Understood the importance of Logistic Regression with respect to Sigmoid.
   - With the implementation of cost function _J(Θ)_ and Loss function, verified the values positive loss and how loss prediction can be minimized to 1.
   - To implement gradient descent function, understood the concept of how to update the weights and find the cost function _J(Θ)_.
   - PART-1.2: Implemented the gradientDescent function, where the parameters x, y, Θ, α, num_iters are provided.
   - Using which implemented the mathematical equation for the DOT product of x and Θ and stored in logits(_z_).
   - Used the Sigmoid function created in PART-1 to calculate the Sigmoid value for the inputs. 
   - Using which the Cost Function _J(Θ)_ and Updated Weights (_Θ_) are being calculated. 
   - This passed all the unit-test cases as well.

  - PART-2: EXTRACTING THE FEATURES
    - Using the list of tweets, we will be extracting the features and store them in a matrix.
    - This contains a series of positive words and negative words in a tweet, which we will train using logistic regression classifier and then test the classifier on the validation set using unit-test.
    - Implemented extract_features function by providing the _tweet_ obtained by using process_tweet function, _freqs_ obtained by using build_freqs function from utils.py. 
    - Iterated through each word in the array word_l obtained from process_tweet.
    - Checked for each word through the dictionary _freqs_ and wherever the word had a match within the pair obtained from the dictionary and the label was 1.0, used its _frequency_ value from dictionary by adding to X[0,1], if the label was 0.0, used its _frequency_ value from dictionary by adding to X[0,2].
    - This passed all the unit-test cases as well.
  
  - PART-3: TRAINING THE MODEL
    - To train the model, the features for all training examples from the dataset are being stacked into a matrix X, by using extract_features function that we implemented in PART-2.
    - All the training labels obtained as y_train corresponding to X are saved as Y.
    - Applied gradient_descent, implemented in PART-1.2, by providing necessary parameter values X, Y, _Θ_, _α_ and num_iters, where _α_ is 1e-9 and num_iters is 1500.
    - This gave us the Cost Function after training and Resulting vector of weights.

  - PART-4: TESTING LOGISTIC REGRESSION
    - To test the Logistic Regression created in PART-1, some input is needed to the model for a good prediction.
    - We will create a function called predict_tweet, which will take inputs _tweet_, _freqs_ and _Θ_.
    - We will use extract_features function to extract _X_ by providing _tweet_ and _freqs_ to the function.
    - Then using Sigmoid function we found y_pred by providing _Z_ which is DOT product of _X_ and _Θ_.
    - This passed all the unit-test cases as well.
    - ### IMPLEMENTATION WITH REAL TEST DATA FROM DATASET
    - Extracted all tweets overs for each iteration through test_x.
    - Calculated y_pred using predict_tweet function by providing _tweet_, _freqs_ and _Θ_.
    - For every y_pred which is > 0.5, y_hat is appended with 1.0, else appended with 0.0.
    - Since y_hat is a list, so it has to be converted to an numpy array by using np.array().
    - Similarly, for test_y, since its a 1-dimensional array, so used np.squueze() to convert to a numpy array.
    - Since for both test_y and y_hat, the size of the numpy arrays are equal, so using one for each loop, compared each numpy array values with each other over iterations through m (_Total Number of Tweets_), the places where there was match over both numpy arrays (y_hat and test_y). A _count_ variable was incremented by 1.
    - Used np.float64 to calculate the accuracy by using count and m. Which gave the accuracy.
    - This passed all the unit-test cases as well.

<br><br>

- Partly implemented:
  - utils.py which contains process_tweet and build_freqs has not been implemented, it was provided.
  - ws_unittest.py was also not implemented as part of assignment to pass all unit-tests for the graded functions().

<br><br>

- Bugs
  - No bugs found!

<br><br>


## Reflections

- Assignment is very good. Gives a thorough understanding of the basis of Logistic Regression and twitter sentiment analysis.
- Would love to see more like this.


## Output

### output

<pre>
</br></br>
    Out[1] - True
    Out[7] - train_y.shape = (8000, 1)
            test_y.shape = (2000, 1)
    Out[8] - type(freqs) = <class 'dict'>
                len(freqs) = 11428
          Expected output
            type(freqs) = <class 'dict'>
                len(freqs) = 11436
    Out[9] - This is an example of a positive tweet: 
              #FollowFriday @France_Inte @PKuchly57 @Milipol_Paris for being top engaged members in my community this week :)

            This is an example of the processed version of the tweet: 
              ['followfriday', 'top', 'engag', 'member', 'commun', 'week', ':)']
          Expected output
            This is an example of a positive tweet: 
            #FollowFriday @France_Inte @PKuchly57 @Milipol_Paris for being top engaged members in my community this week :)

            This is an example of the processes version: 
              ['followfriday', 'top', 'engag', 'member', 'commun', 'week', ':)']
PART-1: LOGISTIC REGRESSION
  Part-1.1: Sigmoid
    Out[11] - SUCCESS!
              CORRECT!
    Out[12] - All tests passed.
  Part-1.2: Cost function and Gradient
    Out[13] - 9.210340371976294
    Out[14] - 9.210340371976182
    Out[16] - The cost after training is 0.67094970.
              The resulting vector of weights is [4.1e-07, 0.00035658, 7.309e-05]
            Expected output
              The cost after training is 0.67094970.
              The resulting vector of weights is [4.1e-07, 0.00035658, 7.309e-05]
    Out[17] - All tests passed.
PART-2: EXTRACTING THE FEATURES
  Out[19] - [[1.000e+00 3.133e+03 6.100e+01]]
          Expected output
            [[1.000e+00 3.133e+03 6.100e+01]]
  Out[20] - [[1. 0. 0.]]
          Expected output
            [[1. 0. 0.]]
PART-3: TRAINING YOUR MODEL
  Out[22] - The cost after training is 0.22521260.
            The resulting vector of weights is [6e-08, 0.0005382, -0.0005583]
          Expected Output:
            The cost after training is 0.22522315.
            The resulting vector of weights is [6e-08, 0.00053818, -0.0005583]
PART-4: TEST YOUR LOGISTIC REGRESSION
  Out[24] - I am happy -> 0.519275
            I am bad -> 0.494347
            this movie should have been great. -> 0.515980
            great -> 0.516065
            great great -> 0.532097
            great great great -> 0.548063
            great great great great -> 0.563930
          Expected Output:
            I am happy -> 0.519275
            I am bad -> 0.494347
            this movie should have been great. -> 0.515979
            great -> 0.516065
            great great -> 0.532096
            great great great -> 0.548062
            great great great great -> 0.563929
  Out[25] - array([[0.83110766]])
  Out[26] - All tests passed.
  Out[28] - Logistic regression model's accuracy = 0.9950
          Expected Output:
            0.9950
            Pretty good!
  Out[29] - All tests passed.
PART-5: ERROR ANALYSIS
  OUt[30] - Label Predicted Tweet
            THE TWEET IS: @MarkBreech Not sure it would be good thing 4 my bottom daring 2 say 2 Miss B but Im gonna be so stubborn on mouth soaping ! #NotHavingit :p
            THE PROCESSED TWEET IS: ['sure', 'would', 'good', 'thing', '4', 'bottom', 'dare', '2', 'say', '2', 'miss', 'b', 'im', 'gonna', 'stubborn', 'mouth', 'soap', 'nothavingit', ':p']
            1	0.48942982	b'sure would good thing 4 bottom dare 2 say 2 miss b im gonna stubborn mouth soap nothavingit :p'
            THE TWEET IS: I'm playing Brain Dots : ) #BrainDots
            http://t.co/UGQzOx0huu
            THE PROCESSED TWEET IS: ["i'm", 'play', 'brain', 'dot', 'braindot']
            1	0.48418982	b"i'm play brain dot braindot"
            THE TWEET IS: I'm playing Brain Dots : ) #BrainDots http://t.co/aOKldo3GMj http://t.co/xWCM9qyRG5
            THE PROCESSED TWEET IS: ["i'm", 'play', 'brain', 'dot', 'braindot']
            1	0.48418982	b"i'm play brain dot braindot"
            THE TWEET IS: I'm playing Brain Dots : ) #BrainDots http://t.co/R2JBO8iNww http://t.co/ow5BBwdEMY
            THE PROCESSED TWEET IS: ["i'm", 'play', 'brain', 'dot', 'braindot']
            1	0.48418982	b"i'm play brain dot braindot"
            THE TWEET IS: off to the park to get some sunlight : )
            THE PROCESSED TWEET IS: ['park', 'get', 'sunlight']
            1	0.49636406	b'park get sunlight'
            THE TWEET IS: @msarosh Uff Itna Miss karhy thy ap :p
            THE PROCESSED TWEET IS: ['uff', 'itna', 'miss', 'karhi', 'thi', 'ap', ':p']
            1	0.48250522	b'uff itna miss karhi thi ap :p'
            THE TWEET IS: @phenomyoutube u probs had more fun with david than me : (
            THE PROCESSED TWEET IS: ['u', 'prob', 'fun', 'david']
            0	0.50988296	b'u prob fun david'
            THE TWEET IS: pats jay : (
            THE PROCESSED TWEET IS: ['pat', 'jay']
            0	0.50040366	b'pat jay'
            THE TWEET IS: my beloved grandmother : ( https://t.co/wt4oXq5xCf
            THE PROCESSED TWEET IS: ['belov', 'grandmoth']
            0	0.50000002	b'belov grandmoth'
            THE TWEET IS: Sr. Financial Analyst - Expedia, Inc.: (#Bellevue, WA) http://t.co/ktknMhvwCI #Finance #ExpediaJobs #Job #Jobs #Hiring
            THE PROCESSED TWEET IS: ['sr', 'financi', 'analyst', 'expedia', 'inc', 'bellevu', 'wa', 'financ', 'expediajob', 'job', 'job', 'hire']
            0	0.50648699	b'sr financi analyst expedia inc bellevu wa financ expediajob job job hire'
PART-6: PREDICT YOUR OWN TWEET
  MY_TWEET - 'Another major improvement in timeline refresh speed just released – now 10X faster than a few months ago'
  
  Out[31] - ['anoth', 'major', 'improv', 'timelin', 'refresh', 'speed', 'releas', '–', '10x', 'faster', 'month', 'ago']
            [[0.49993232]]
            Negative sentiment
</br></br>
</pre>