# utl-using-nonlinear-optimization-to-fit-an-arc-tangent-curve-wps-r-python
Given x y data we want to find the optimum value for a.  y = 2*atan(x/a)/pi
    %let pgm=utl-using-nonlinear-optimization-to-fit-an-arc-tangent-curve-wps-r-python;

    github
    https://tinyurl.com/uf4pse5m
    https://github.com/rogerjdeangelis/utl-using-nonlinear-optimization-to-fit-an-arc-tangent-curve-wps-r-python

    Fitting a non-linear equation y = 2*atan(x/a)/pi wps r sympy

    Given x y data we want to find the optimum value for a.  y = 2*atan(x/a)/pi

     SOLUTIONS

       1 Differentiate tangent equation y = 2*atan(x/a)/p with respect to a.
         We use symoy to symbolicall differentiate
         Optimization algorithms can use the divitive to more quickly find the solution

       2 wps proc r

       3 wps proc nlin

       4 related repo on end

    see
    https://stackoverflow.com/questions/50189130/approximating-a-curve-with-arctan

    Weihuang Wong profile
    https://stackoverflow.com/users/6455166/weihuang-wong

           BEST FIT

            y      =  2*atan(x/a)/pi
          dy/da    = -2*x/(pi*a**2*(1 + x**2/a**2))

            0       20000     40000     60000
         ---+---------+---------+---------+--
         |                                  |
         | Optimum fitted equation          |
         |                                  |
    1.00 + y = 2*atan(x/a)/pi   .  * *      + 1.00
         |                 . *              |
         |               *                  |
         |             ,                    |
         |            *                     |
    0.75 +           *                      + 0.75
         |          *                       |
         |         * Optimum value for a    |
      Y  |        *                         |   Y
         |       * WPS proc NLIN   a=7069.4 |
    0.50 +       * WPS/Proc R      a=7069.4 + 0.50
         |      :                           |
         |      *                           |
         |     *                            |
         |     *                            |
    0.25 +    *                             + 0.25
         |    *                             |
         |   *                              |
         |   *                              |
         |                                  |
    0.00 +                                  + 0.00
         ---+---------+---------+---------+--
            0       20000     40000     60000

    /*       _ _  __  __                     _   _       _
    / |   __| (_)/ _|/ _| ___ _ __ ___ _ __ | |_(_) __ _| |_ ___
    | |  / _` | | |_| |_ / _ \ `__/ _ \ `_ \| __| |/ _` | __/ _ \
    | | | (_| | |  _|  _|  __/ | |  __/ | | | |_| | (_| | ||  __/
    |_|  \__,_|_|_| |_|  \___|_|  \___|_| |_|\__|_|\__,_|\__\___|

    */

    %utl_submit_wps64x("
    proc python;
    submit;
    from sympy import *;
    import pandas as pd;
    from sympy import *;
    x, a = symbols('x,a', real=True);
    dif=diff(2*atan(x/a)/pi, a);
    print(dif);
    endsubmit;
    run;quit;
    ");


    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /* The WPS System                                                                                                         */
    /*                                                                                                                        */
    /* The PYTHON Procedure                                                                                                   */
    /*                                                                                                                        */
    /* -2*x/(pi*a**2*(1 + x**2/a**2))                                                                                         */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    options validvarname=upcase;
    libname sd1 "d:/sd1";
    data sd1.have;
      input x y @@;
    cards4;
    1000 0.101 2000 0.169 3000 0.209 4000 0.256 5000 0.289 6000 0.373 7000 0.391 8000 0.418 9000 0.477 10000 0.528
    11000 0.579 12000 0.570 13000 0.602 14000 0.657 15000 0.690 16000 0.720 17000 0.747 18000 0.764 19000 0.781
    20000 0.811 21000 0.842 22000 0.847 23000 0.864 24000 0.889 25000 0.871 26000 0.894 27000 0.897 28000 0.915
    29000 0.926 30000 0.931 31000 0.932 32000 0.940 33000 0.950 34000 0.963 35000 0.956 36000 0.967 37000 0.967
    38000 0.963 39000 0.971 40000 0.980 41000 0.986 42000 0.988 43000 0.986 44000 0.985 45000 0.993 46000 0.992
    47000 0.994 48000 0.991 49000 0.995 50000 0.993
    ;;;;
    run;quit;

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*  The WPS System                                                                                                        */
    /*                                                                                                                        */
    /*       X      Y                                                                                                         */
    /*  1 1000  0.101                                                                                                         */
    /*  2 2000  0.169                                                                                                         */
    /*  3 3000  0.209                                                                                                         */
    /*  4 4000  0.256                                                                                                         */
    /*  5 5000  0.289                                                                                                         */
    /*  6 6000  0.373                                                                                                         */
    /*  ....                                                                                                                  */
    /* 45 45000 0.993                                                                                                         */
    /* 46 46000 0.992                                                                                                         */
    /* 47 47000 0.994                                                                                                         */
    /* 48 48000 0.991                                                                                                         */
    /* 49 49000 0.995                                                                                                         */
    /* 50 50000 0.993                                                                                                         */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*___
    |___ \  __      ___ __  ___   _ __  _ __ ___   ___   _ __
      __) | \ \ /\ / / `_ \/ __| | `_ \| `__/ _ \ / __| | `__|
     / __/   \ V  V /| |_) \__ \ | |_) | | | (_) | (__  | |
    |_____|   \_/\_/ | .__/|___/ | .__/|_|  \___/ \___| |_|
                     |_|         |_|
    */

    proc datasets lib=work nolist nodetails mt=cat;
      delete sasmac1 sasmac2 sasmac3 sasmac4;
    run;quit;

    %symbel a / nowarn;

    %utl_submit_wps64x('
    libname sd1 "d:/sd1";
    proc r;
    export data=sd1.have r=have;
    submit;
    library(haven);
    have;
    xs<-have$X;
    ys<-have$Y;
    form <- function(a, xs) 2 * atan(xs / a) / pi;
    loss <- function(a, xs, data) mean((form(a, xs) - ys)^2);
    optimized <- optim(1000, loss, xs = xs, data = data, method = "Brent", lower = 1, upper = 10000);
    a <- as.character(optimized$par);
    a;
    writeClipboard(a);
    endsubmit;
    run;quit;
    ',return=a);

    %put Optimum &=a;

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*  %put Optimum &=a;                                                                                                     */
    /*                                                                                                                        */
    /*  Optimum A = 7069.41964845207                                                                                          */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*____                                _ _
    |___ /   _ __  _ __ ___   ___   _ __ | (_)_ __
      |_ \  | `_ \| `__/ _ \ / __| | `_ \| | | `_ \
     ___) | | |_) | | | (_) | (__  | | | | | | | | |
    |____/  | .__/|_|  \___/ \___| |_| |_|_|_|_| |_|
            |_|
    */

    proc datasets lib=work nolist nodetails mt=cat;
      delete sasmac1 sasmac2 sasmac3 sasmac4;
    run;quit;

    %symdel a / nowarn;

    libname sd1 "d:/sd1";
    %utl_submit_wps64x("
    libname sd1 'd:/sd1';
      proc nlin best=10  method=marquardt data=sd1.have;
        parms a=500 to 20000 by 50;
        model y=2*atan(x/a)/constant('pi');
        der.a=-2*x/(constant('pi')*a**2*(1 + x**2/a**2));
        output out=want parms=a;
      run;quit;
      proc print data=want;
      run;quit;
      /*---- Clipboard is sent to a macro variable a Pass to parent.           ----*/
      filename clp clipbrd;
      data _null_;
        set want(obs=1);
        file clp;
        put a;
        putlog a;
      run;quit;
    ",return=a);

    %put Optimum &=a;


    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*  %put Optimum &=a;                                                                                                     */
    /*                                                                                                                        */
    /*  Optimum A=7069.4145858                                                                                                */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*
     _ __ ___ _ __   ___  ___
    | `__/ _ \ `_ \ / _ \/ __|
    | | |  __/ |_) | (_) \__ \
    |_|  \___| .__/ \___/|___/
             |_|
    */

    https://github.com/rogerjdeangelis/utl-calculating-the-cube-root-of-minus-one-with-drop-down-to-python-symbolic-math-sympy
    https://github.com/rogerjdeangelis/utl-symbolic-algebraic-simplification-of-a-polynomial-expressions-sympy
    https://github.com/rogerjdeangelis/utl-sympy-technique-for-symbolic-integration-of-bivariate-density-function

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
