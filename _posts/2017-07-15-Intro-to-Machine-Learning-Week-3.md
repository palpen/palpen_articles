---
layout: post
title: Intro to Machine Learning Week 3
---

## 


## Some other useful notes

Matlab function that creates the polynomial terms (nth degree) of the features X1 and X2 (e.g. X1, X2, X1.^2, X2.^2, X1*X2, X1*X2.^2, etc..):

    function out = mapFeature(X1, X2, n)
        degree = n;
        out = ones(size(X1(:,1)));
        for i = 1:degree
            for j = 0:i
                out(:, end+1) = (X1.^(i-j)).*(X2.^j);
            end
        end
    end
