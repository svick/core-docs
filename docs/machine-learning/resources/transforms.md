---
title: Data transforms
description: Explore the different data transforms supported in ML.NET.
ms.date: 10/16/2018
---
# Data transforms

The following tables contain information about all of the data transforms supported in ML.NET (select the data transform type to navigate to the corresponding table):

* [Categorical](#categorical)
* [Combiners and segregators](#combiners-and-segregators)
* [Feature selection](#feature-selection)
* [Featurizers](#featurizers)
* [Label parsing](#label-parsing)
* [Missing Values](#missing-values)
* [Normalization](#normalization)
* [Row filters](#row-filters)
* [Schema](#schema)
* [Text processing and featurization](#text-processing-and-featurization)
* [Miscellaneous](#miscellaneous)

> [!NOTE]
> ML.NET is currently in Preview. Not all data transforms are currently supported. To submit a request for a certain transform, open an issue in the [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) GitHub repository.

## Categorical

| Transform | Definition |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CategoricalHashOneHotVectorizer> | Encodes the categorical variable with hash-based encoding. |
| <xref:Microsoft.ML.Legacy.Transforms.CategoricalOneHotVectorizer> | Encodes the categorical variable with one-hot encoding based on a term dictionary. |

## Combiners and segregators

| Transform | Definition |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CombinerByContiguousGroupId> | Groups values of a scalar column into a vector based on a contiguous group ID. |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureCombiner> | Combines all the features into one feature column. |
| <xref:Microsoft.ML.Legacy.Transforms.ManyHeterogeneousModelCombiner> | Combines a sequence of TransformModels and a PredictorModel into a single PredictorModel. |
| <xref:Microsoft.ML.Legacy.Transforms.ModelCombiner> | Combines a sequence of TransformModels into a single model. |
| <xref:Microsoft.ML.Legacy.Transforms.Segregator> | Ungroups vector columns into sequences of rows; the inverse of Group transform. |
| <xref:Microsoft.ML.Legacy.Transforms.TwoHeterogeneousModelCombiner> | Combines a TransformModel and a PredictorModel into a single PredictorModel. |

## Feature selection

| Transform | Definition |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureSelectorByCount> | Selects the slots for which the count of non-default values is greater than or equal to a threshold. |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureSelectorByMutualInformation> | Selects the top k slots across all specified columns ordered by their mutual information with the label column. |

## Featurizers

| Transform | Definition |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.HashConverter> | Converts column values into hashes. This transform accepts both numeric and text inputs, both single and vector-valued columns. |
| <xref:Microsoft.ML.Legacy.Transforms.TreeLeafFeaturizer> | Trains a tree ensemble, or loads it from a file, then maps a numeric feature vector to three outputs: 1. A vector containing the individual tree outputs of the tree ensemble. 2. A vector indicating the leaves that the feature vector falls on in the tree ensemble. 3. A vector indicating the paths that the feature vector falls on in the tree ensemble. If both a model file and a trainer are specified, the vector will use the model file. If neither are specified, the vector will train a default FastTree model. This can handle key labels by training a regression model towards their optionally permuted indices. |

## Label parsing

| Transform | Definition |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.Dictionarizer> | Converts input values (words, numbers, etc.) to index in a dictionary. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelColumnKeyBooleanConverter> | Transforms the label to either key or bool (if needed) to make it suitable for classification. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelIndicator> | Label remapper used by OVA. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelToFloatConverter> | Transforms the label to float to make it suitable for regression. |
| <xref:Microsoft.ML.Legacy.Transforms.PredictedLabelColumnOriginalValueConverter> | Transforms a predicted label column to its original values, unless it is of type bool. |

## Missing values

| Transform | Definition |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueHandler> | Handle missing values by replacing them with either the default value or the mean/min/max value (for non-text columns only). An indicator column can optionally be concatenated, if the input column type is numeric. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueIndicator> | Create a boolean output column with the same number of slots as the input column, where the output value is true if the value in the input column is missing. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValuesDropper> | Removes NAs from vector columns. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValuesRowDropper> | Filters out rows that contain missing values. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueSubstitutor> | Create an output column of the same type and size of the input column, where missing values are replaced with either the default value or the mean/min/max value (for non-text columns only). |

## Normalization

| Transform | Definition |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.BinNormalizer> | The values are assigned into equidensity bins and a value is mapped to its bin_number / number_of_bins. |
| <xref:Microsoft.ML.Legacy.Transforms.ConditionalNormalizer> | Normalize the columns only if needed. |
| <xref:Microsoft.ML.Legacy.Transforms.GlobalContrastNormalizer> | Performs a global contrast normalization on input values: Y = (s * X - M) / D, where s is a scale, M is mean and D is either L2 norm or standard deviation. | 
| <xref:Microsoft.ML.Legacy.Transforms.LogMeanVarianceNormalizer> | Normalizes the data based on the computed mean and variance of the logarithm of the data. |
| <xref:Microsoft.ML.Legacy.Transforms.LpNormalizer> | Normalize vectors (rows) individually by rescaling them to the unit norm (L2, L1 or LInf). Performs the following operation on a vector X: Y = (X - M) / D, where M is mean and D is either the L2 norm, the L1 norm, or the LInf norm. |
| <xref:Microsoft.ML.Legacy.Transforms.MeanVarianceNormalizer> | Normalizes the data based on the computed mean and variance of the data. |
| <xref:Microsoft.ML.Legacy.Transforms.MinMaxNormalizer> | Normalizes the data based on the observed minimum and maximum values of the data. |

## Row Filters

| Transform | Definition |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.RowRangeFilter> | Filters a dataview on a column of type Single, Double or Key (contiguous). Keeps the values that are in the specified min/max range. NaNs are always filtered out. If the input is a Key type, the min/max are considered percentages of the number of values. |
| <xref:Microsoft.ML.Legacy.Transforms.RowSkipAndTakeFilter> | Allows limiting input to a subset of rows at an optional offset. Can be used to implement data paging. |
| <xref:Microsoft.ML.Legacy.Transforms.RowSkipFilter> | Allows limiting input to a subset of rows by skipping a number of rows. |
| <xref:Microsoft.ML.Legacy.Transforms.RowTakeFilter> | Allows limiting input to a subset of rows by taking N first rows. |

## Schema

| Transform | Definition |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> | Concatenates two columns of the same item type. |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnCopier> | Duplicates columns from the dataset.|
| <xref:Microsoft.ML.Legacy.Transforms.ColumnDropper> | Drops columns from the dataset. |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnSelector> | Selects a set of columns, dropping all others. |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnTypeConverter> | Converts a column to a different type, using standard conversions. |
| <xref:Microsoft.ML.Legacy.Transforms.KeyToTextConverter> | KeyToValueTransform utilizes KeyValues metadata to map key indices to the corresponding values in the KeyValues metadata. |
| <xref:Microsoft.ML.Legacy.Transforms.NGramTranslator> | Produces a bag of counts of ngrams (sequences of consecutive values of length 1-n) in a given vector of keys. It does so by building a dictionary of ngrams and using the id in the dictionary as the index in the bag. | 
| <xref:Microsoft.ML.Legacy.Transforms.OptionalColumnCreator> | If the source column does not exist after deserialization, create a column with the right type and default values. |

## Text processing and featurization

| Transform | Definition |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CharacterTokenizer> | Character-oriented tokenizer where text is considered a sequence of characters. |
| <xref:Microsoft.ML.Legacy.Transforms.TextFeaturizer> | A transform that turns a collection of text documents into numerical feature vectors. The feature vectors are normalized counts of (word and/or character) ngrams in a given tokenized text. |
| <xref:Microsoft.ML.Legacy.Transforms.TextToKeyConverter> | Converts input values (words, numbers, etc.) to index in a dictionary. |
| <xref:Microsoft.ML.Legacy.Transforms.WordEmbeddings> | A transform that converts vectors of text tokens into numeric vectors using a pre-trained model. For more information about the technique, see the [Word embedding](https://en.wikipedia.org/wiki/Word_embedding) Wikipedia page. |
| <xref:Microsoft.ML.Legacy.Transforms.WordTokenizer> | The input to this transform is text, and the output is a vector of text containing the words (tokens) in the original text. The separator is space, but any other character (or multiple characters) can be specified. |

## Miscellaneous

| Transform | Definition |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.ApproximateBootstrapSampler> | Approximate bootstrap sampling. |
| <xref:Microsoft.ML.Legacy.Transforms.BinaryPredictionScoreColumnsRenamer> | For binary prediction, renames the PredictedLabel and Score columns to include the name of the positive class.|
| <xref:Microsoft.ML.Legacy.Transforms.DataCache> | Caches using the specified cache option. |
| <xref:Microsoft.ML.Legacy.Transforms.DatasetScorer> | Scores a dataset with a predictor model. |
| <xref:Microsoft.ML.Legacy.Transforms.DatasetTransformScorer> | Scores a dataset with a transform model. |
| <xref:Microsoft.ML.Legacy.Transforms.NoOperation> | Does nothing. |
| <xref:Microsoft.ML.Legacy.Transforms.RandomNumberGenerator> | Adds a column with a generated number sequence. |
| <xref:Microsoft.ML.Legacy.Transforms.ScoreColumnSelector> | Selects only the last score columns and the extra columns specified in the arguments. |
| <xref:Microsoft.ML.Legacy.Transforms.Scorer> | Turns the predictor model into a transform model. |
| <xref:Microsoft.ML.Legacy.Transforms.SentimentAnalyzer> | Uses a pretrained sentiment model to score input strings. |
| <xref:Microsoft.ML.Legacy.Transforms.TrainTestDatasetSplitter> | Splits the dataset into train and test sets. |
