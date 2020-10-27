1. 数据格式转换, 已经使用 libsvm/tools/checkdata.py 验证完毕
    python3 ./libsvm/tools/checkdata.py totaldata

todo: 

2. scale
    ./libsvm/svm-scale  -s scaling_parameter traindata >> scaled_traindata
    ./libsvm/svm-scale  -r scaling_parameter testdata >> scaled_testdata

4. binary classification: 
    要求:
        training data 10-fold cross validation 
        polynomial kernel: 
        参数: 
            degree = 1,2,3,4
            C loss function, C = 2^-k , ... , 2^k, 
            k 的选择要求我们可以在validation error中看到很大的改变.
            其它参数默认
        输出: 
            for d in degrees:
                plot initialize
                for C in Cs: 
                    plot(average cross-validation-error ± std)
                plot.show()
    实现方式: svm-train
        -t 1                    代表polynomial kernel
        -d 1,2,3,4              代表degree
        -c 2^{-k},...,2^{k}     代表k的值
        -v 10.                  10 fold-validation
        


    svm-train 参数解释: 
    -v n: 代表着 n-fold crossvalidation




7. plot average cross-validation error ± 1 std, as a function of C: C = 2^-k, ... , 2^k. 而其它参数等于libsvm的默认值. 

8. (C*,d*) 是从上面找到的最优参数, 
    画出 ten-fold cross-validation error,   as a function of d
    画出 test-error                         as a function of d
    画出 average # of support vector        as a function of d
        多少supp在margin hyper plane上?

9. sparsity of supp VS notion of margin
    考虑maximize sparsity 等价于 minimize 
    等等...

10. 程序之output:
    optimization finished, #iter = 219:             iter    应该是指sample大小
    nu = 0.431030                                   nu      应该是在nu-svm问题中的等价于 c 的参数. 
    obj = -100.877286,                              obj     optimal objective value of dual SVM problem
    rho = 0.424632                                  rho     svm问题中的 b
    nSV = 132,                                      nSV     supp vect的个数
    nBSV = 107                                      nBSV    bounded supp vect的个数
    Total nSV = 132

11. read results:
    1. trials[i][0] = iter
    2. trials[i][1] = nu
    3. trials[i][2] = obj
    4. trials[i][3] = rho
    5. trials[i][4] = nSV
    6. trials[i][5] = nBSV
    7. trials[i][6] = Total nSV

    values needed: 

    1. accuracy
    2. standard deviation of accuracy
    3. test error
    4. average # of supp vect
    5. supp on the margin hyperplanes`