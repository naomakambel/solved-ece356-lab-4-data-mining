Download Link: https://assignmentchef.com/product/solved-ece356-lab-4-data-mining
<br>
<h1>1           Classification Tasks</h1>

In this lab, you will analyze the Sean Lahman data set and construct classifiers to predict the values of certain target variables related to the nomination and induction of players into the Baseball Hall of Fame. In general, players in the database can be grouped into three categories:

<ol>

 <li>inducted into the Baseball Hall of Fame (player appears in HallOfFame table and inducted = ’Y’)</li>

 <li>nominated for the Baseball Hall of Fame but not inducted (player appears in HallOfFame table and inducted = ’N’)</li>

 <li>not nominated for the Baseball Hall of Fame (player does not appear in HallOfFame table)</li>

</ol>

Using combinations of these three categories, we will formulate two prediction problems, as explained in more detail below. <strong>The classifiers for these problems are to be constructed using input variables <u>outside </u>of the </strong>HallOfFame <strong>table. </strong>For example, this means that the voting data (e.g., ballots, needed, and votes) cannot be used as inputs to the classifier. The HallOfFame table should only be used to assign the correct classification label during training.

<strong>Task A: </strong>Given an arbitrary player, predict whether the player will be nominated for the Baseball Hall of Fame. The classification label is True if a player belongs to category 1 or 2 above, and False otherwise.

<strong>Task B: </strong>Given a player who has been nominated for the Baseball Hall of Fame, predict whether the player will be inducted. The classification label is True if a player belongs to category 1 above, and False is the player belongs to category 2 above. Players in category 3 are not considered at all in this task.

<h1>2           Methodology</h1>

For a prediction problem, we start by identifying the features that will be used as input variables. In <em>feature selection</em>, features in the data set that may be suitable for the classification problem are chosen. Features that are redundant, or irrelevant to the problem, are dropped at this stage.

Since we are dealing with a relational database as the input data set, each feature is an attribute of some table. Thus, feature selection requires writing SQL code that joins the Player ID with other attributes that may be useful for prediction, as well as the correct classification label. The HallOfFame table should only be used to compute the latter. The output of the SQL query must be saved as human-readable CSV (comma-separate values) text file that can be imported into the data mining tool. Produce a separate file for Task A and Task B, and format each CSV file so that the player ID (string) is in the first column, and the classification label (Boolean) is in the last column. The CSV files must include a header row of the following form: <em>playerID,feature</em>1<em>,feature</em>2<em>,….,featureN,class</em>.

After feature selection, you will <strong>construct decision tree classifiers </strong>using MATLAB or Python to solve the prediction problems defined earlier as Task A and Task B. To evaluate your decision trees, you will divide the data set into two separate parts: training set (80%) and the testing set (20%). The data mining tool will then build the decision tree model over the training set, and validate it using the testing set. The validation results will be summarized using a <strong>confusion matrix</strong>, which is the basis for computing correctness measures such as accuracy, recall, precision, and the F1 score. You will tune the decision tree by experimenting with different hyperparameters (e.g., impurity measure, maximum depth, etc.) to optimize its predictive power, and reflect on your design choices.

<h1>3           Deliverables</h1>

The expected submission for this lab is a collection of files, to be submitted electronically using the Lab 4 dropbox in LEARN. Either submit the files individually, or submit them as a single zip archive. Each deliverable is described in more detail below.

<ol>

 <li><strong>Report</strong></li>

</ol>

Write a report on your findings, and submit it as a single PDF file that includes all supporting tables and figures. The report should be approximately 2000–2500 words long. The report must include the following content:

<ul>

 <li>Include the names, Waterloo emails, and student numbers of all group members on the title page.</li>

 <li>For each classification task, compute the total number of instances in the data set, as well as the number of instances in each class. Present the SQL queries used to compute these numbers.</li>

 <li>Describe any data cleansing issues encountered in the data set, and their solutions. Be creative.</li>

 <li>Explain your initial selection of features from the database. Provide rationale for each feature you selected.</li>

 <li>Explain how exactly you sampled the training and testing subsets. Justify your sampling strategy.</li>

 <li>For each of the two prediction tasks defined earlier, report on the validation results. At minimum, present the confusion matrix as a table, and indicate the accuracy obtained. Justify any other correctness measures discussed. Why should one measure be preferred over another?</li>

 <li>For each prediction problem, explain how you tuned the hyperparameters to obtain alternative solutions that achieve different trade-offs with respect to the complexity of the model (e.g., size of the tree) versus its predictive power (e.g., accuracy). Which of the features you selected initially are actually used by your alternative solutions? How did you address the problem of over-fitting?</li>

 <li>For the models discussed in the previous point, present illustrations of the decision trees. The illustrations must show clearly the attributes used in different splits, as well a structural properties such as the depth, branching factor, and number of leaf nodes. You may copy and paste visualizations from the data mining tool.</li>

 <li>Check the report carefully for spelling and grammar mistakes. Polish your writing.</li>

</ul>

<ol start="2">

 <li><strong>SQL code</strong></li>

</ol>

Submit the SQL scripts you used to export the selected features and classification labels for each prediction task into CSV files.

<ol start="3">

 <li><strong>CSV file</strong></li>

</ol>

Submit the CSV files produced by your SQL scripts, one for each task. Use a correctly formatted header row, as explained earlier.

<ol start="4">

 <li><strong>MATLAB or Python code</strong></li>

</ol>

Submit the MATLAB or Python code you use to construct your decision tree classifiers and output their validation results.

Your submission will be checked for completion, and also assessed for quality. Highest grades will be awarded to submissions that are technically deep and well presented.

<h1>4           MATLAB reference material</h1>

<table width="681">

 <tbody>

  <tr>

   <td width="262"><strong>MATLAB function</strong></td>

   <td width="419"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="262"><strong>MODEL = FITCTREE (TBL, Y)</strong></td>

   <td width="419">This function is used to train the Decision Trees model in MATLAB.It needs two arguments: TBL refers to the data with the actual data values, and Y are the classificationlabels, provided as a part of the training dataset. It returns a Decision Tree model thatcan be used when testing the algorithm. For further details, you can refer to the MathWorks R website:<a href="https://www.mathworks.com/help/stats/fitctree.html">https://www.mathworks.com/help/stats/fitctree.html</a><a href="https://www.mathworks.com/help/stats/fitctree.html">.</a></td>

  </tr>

  <tr>

   <td width="262"><strong>YP = PREDICT (MODEL, DATA)</strong></td>

   <td width="419">This MATLAB function can be used to predict the output of a trained model.The two arguments are the MODEL which is the model youwould have achieved while training the data, and DATArefers to the test data on which the model needs to run.The ground truth of the testing sample is thus only used for evaluation purposes when you will be calculating accuracy of the results. For further details, you can refer to the MathWorks R website:<a href="https://www.mathworks.com/help/stats/compactclassificationtree.predict.html">https://www.mathworks.com/help/stats/compactclassificationtree.predict.html</a><a href="https://www.mathworks.com/help/stats/compactclassificationtree.predict.html">.</a></td>

  </tr>

 </tbody>

</table>

Table 1: MATLAB functions for constructing decision tree classifiers.

<table width="622">

 <tbody>

  <tr>

   <td width="143"><strong>MATLAB function</strong></td>

   <td width="479"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="143"><strong>loss</strong></td>

   <td width="479">Calculates the classification error of the model generated</td>

  </tr>

  <tr>

   <td width="143"><strong>confusionmat</strong></td>

   <td width="479">Indicates how many labels were correctly classified and how many of them are inaccurate</td>

  </tr>

  <tr>

   <td width="143"><strong>view</strong></td>

   <td width="479">Gives the textual and visual representation of the Decision tree model, including the split attribute, split condition and the path it takes inthe tree (for example, left child or right child, etc) as a result of that condition.</td>

  </tr>

 </tbody>

</table>

Table 2: MATLAB functions for validating and visualizing decision tree classifiers.

<table width="635">

 <tbody>

  <tr>

   <td width="202"><strong>MATLAB hyperparameters</strong></td>

   <td width="434"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="202"><strong>MaxNumSplits</strong></td>

   <td width="434">The maximum number of branch node splits is MaxNumSplits per tree. Set a large value for MaxNumSplits to get a deep tree.</td>

  </tr>

  <tr>

   <td width="202"><strong>MinLeafSize</strong></td>

   <td width="434">Each leaf has at least MinLeafSize observations.Set small values of MinLeafSize to get deep trees.The default is 1.</td>

  </tr>

  <tr>

   <td width="202"><strong>MinParentSize</strong></td>

   <td width="434">Each branch node in the tree has at least MinParentSize observations.Set small values of MinParentSize to get deep trees. The default is 10</td>

  </tr>

 </tbody>

</table>

Table 3: MATLAB functions for tuning certain hyperparameters.

<h1>5           Python reference material</h1>

<table width="694">

 <tbody>

  <tr>

   <td width="224"><strong>Python Sklearn function</strong></td>

   <td width="470"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="224"><strong>clf = DecisionTreeClassifier() clf = clf.fit(X </strong><strong>train,y train)</strong></td>

   <td width="470">This function is used to train the Decision Tree models in Python. It needs two arguments: X train refers to the data with the actual data values, and y train are the classificationlabels, provided as a part of the training dataset. It returns a Decision Tree model thatcan be used when testing the algorithm. For further details, you can refer to the scikit-learn website:<a href="https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html">https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html</a><a href="https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html">.</a></td>

  </tr>

  <tr>

   <td width="224"><strong>y pred = clf.predict(X test)</strong></td>

   <td width="470">This function can be used to predict the output of a trained model.The argument X test refers to the test data on which the model needs to run.The ground truth of the testing sample is thus only used for evaluation purposes when you will be calculating accuracy of the results. For an example you can refer to the datacamp tutrorial: website:<a href="https://www.datacamp.com/community/tutorials/decision-tree-classification-pythonl">https://www.datacamp.com/community/tutorials/decision-tree-classification-pythonl</a><a href="https://www.datacamp.com/community/tutorials/decision-tree-classification-pythonl">.</a></td>

  </tr>

 </tbody>

</table>

Table 4: Python Sklearn functions for constructing decision tree classifiers.

<table width="719">

 <tbody>

  <tr>

   <td width="240"><strong>Python Sklearn function</strong></td>

   <td width="479"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="240"><strong>confusion matrix(y true, y pred)</strong></td>

   <td width="479">Indicates how many labels were correctly classified and how many of them are inaccurate</td>

  </tr>

  <tr>

   <td width="240"><strong>clf.plot tree(clf)</strong></td>

   <td width="479">Gives the textual and visual representation of the Decision tree model, including the split attribute, split condition and the path it takes inthe tree (for example, left child or right child, etc) as a result of that condition.</td>

  </tr>

 </tbody>

</table>

Table 5: Python Sklearn functions for validating and visualizing decision tree classifiers.

<table width="722">

 <tbody>

  <tr>

   <td width="239"><strong>Python Sklearn hyperparameters</strong></td>

   <td width="484"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="239"><strong>max depth</strong></td>

   <td width="484">The maximum depth of the tree. If None, then nodes are expanded until all leaves are pure or until all leaves contain less than min samples split samples</td>

  </tr>

  <tr>

   <td width="239"><strong>min </strong><strong>samples split</strong></td>

   <td width="484">The minimum number of samples required to split an internal node.</td>

  </tr>

  <tr>

   <td width="239"><strong>min samples </strong><strong>leaf</strong></td>

   <td width="484">The minimum number of samples required to be at a leaf node.</td>

  </tr>

 </tbody>

</table>

Table 6: Python Sklearn functions for tuning certain hyperparameters.