# find_political_donors

# run instructions

Just run political donation.ipynb file with your own data source.

# question approach

I approach this problem in 4 steps:

Step 1: input data Here, need your own data source, for example, I saved one sample data as "C:\Users\Sissi\Downloads\find-political-donors-master\insight_testsuite\tests\test_1\input\itcont.txt". Extract data.

Step 2: clean data As request, we only need individual donors (OTHER_ID is empty), need donors identity (CMTE_ID is not empty), and need transaction amount(TRANSACTION_AMT is not empty). So drop nonqualified entries first.

Step 3: Do ZIP based part
This step contain 3 things.

First, drop bad-ZIP entries.

Second, create loop for running median. Here, I create 4 variables: Total Number of Transaction (TN_TRAN), Total Amount of Transaction (TA_TRAN), List of Amount of Transaction based on this particular ZIP (LTA_TRAN) and Running Median (RMEDIAN_ZIP). At beginning, Total Number of Transaction equals to 1 for each, Total Amount of Transaction equals to the transaction amount of each, List only contain its own transaction amount, and Running Median eqauls to transaction amount. This is what I do in the first loop. Then the second one, I searched the same ZIP from backwards, because I saved "Total Number of Transaction (TN_TRAN), Total Amount of Transaction (TA_TRAN), List of Amount of Transaction based on this particular ZIP (LTA_TRAN) and Running Median (RMEDIAN_ZIP)" for each row, when meet the most recently same ZIP entry, just plus 1 for Total Number of Transaction, plus this transaction amount for Total Amount of Transaction, add this transaction amount to List of Amount of Transaction, and do running median using List of Amount of Transaction.

Last, write the result into text file. The file contains CMTE_ID, ZIP_CODE (only 5 digits), RMEDIAN_ZIP, TOTNUMBER_TRAN, TOTAMT_TRAN.

Step 4: Do date based part
This step also contain 3 things.

First, drop bad-date entries.
Second, caculate median, sum, and number of transaction based on groups, here is CMTE_ID and TRANSACTION_DT.
Last, write the result into text file. The file contains CMTE_ID, TRANSACTION_DT, MEDIAN_DT, TOTNUMBER_DT, TOTAMT_DT.

