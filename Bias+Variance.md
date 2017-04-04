



<style>

div.cell { /* Tunes the space between cells */
margin-top:1em;
margin-bottom:1em;
}

div.text_cell_render h1 { /* Main titles bigger, centered */
font-size: 2.2em;
line-height:1.4em;
text-align:center;
}

div.text_cell_render h2 { /*  Parts names nearer from text */
margin-bottom: -0.4em;
}


div.text_cell_render { /* Customize text cells */
font-family: 'Times New Roman';
font-size:1.4em;
line-height:1.4em;
padding-left:3em;
padding-right:3em;
}
</style>





# Bias-Variance Tradeoff
## Joby John (11/29/2016)

Many texts show the decomposition of Mean Squared Error (MSE) in *Bias-Variance* components. I have never found a good description of exactly how MSE is decomposed in to the constituent terms of Bias Variance and Irreducible Error. I present this hoping some student finds this useful. The important step in the derivation is to add and subtract $2\:\overline{f}^2$ so that the terms can be grouped in to __Bias$^2$__ and __variance__ terms.

The relationship between the the predictor $X$ and the predicted variable $Y$ is of the form  
$Y = f(X)+\epsilon$. Also, $Var(\epsilon) = \sigma_{\epsilon}^2$, where $\epsilon$ is the *irreducible error*.

### Notation
$\Large f$ - the actual value of the function/variable being estimated  
$\Large \hat{f}$ - the estimated value (a random variable with some distribution)  
$\Large \overline{f}$ - the mean of the estimated value, i.e. $\overline{f} = E(\hat{f})$ 

The error estimate then is:  
$\Large MSE =  E([Y-\hat{f}(X)]^2)$  
        $\Large = E([f(X)+\epsilon - \hat{f}(X)]^2)$, (drop the X's)
        $\Large = E(f^2+\epsilon^2+2 f \epsilon + \hat{f}^2 - 2 (f +\epsilon) \hat{f})$  
        $\Large = E(f^2)+E(\hat{f}^2)+\sigma_{\epsilon}^2 - 2 f E(\hat{f})$  
        (Since $\epsilon$ and $\hat{f}$ are uncorrelated and $E(\epsilon) \approx 0$)  
        $\Large  = E(f^2)+E(\hat{f}^2)+\sigma_{\epsilon}^2 - 2 f \overline{f}$  

Now we add and subtract <font color='red'>$\Large  2\overline{f}^2 $</font>  
         $\Large = E(f^2)+\overline{f}^2-2 \overline{f} \overline{f}+ E(\hat{f}^2)+\overline{f}^2-2 f \overline{f}+\sigma_{\epsilon}^2$  
         $\Large  = E(f^2)+\overline{f}^2-2 f \overline{f}+ E(\hat{f}^2)+\overline{f}^2-2 \overline{f} \overline{f}+\sigma_{\epsilon}^2$  
         $\Large = E(f^2)+E(\overline{f}^2)-E(2 f \overline{f})+ E(\hat{f}^2)+E(\overline{f}^2)$  
         $\:\:\:\:\:\!\Large -2 E(\hat{f}) \overline{f}+\sigma_{\epsilon}^2$  
         $\Large  = E((f-\overline{f})^2)+ E((\hat{f}-\overline{f})^2)+\sigma_{\epsilon}^2$
         $\Large = Bias^2+Variance+Irreducible\: error$


