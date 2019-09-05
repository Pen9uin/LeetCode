### v1
```
//二分法
double Sqrt(double A)
{
    double a = 0.0, b = A + 0.25, m;
	
    while(b - a > 1e-6)
    {
        m = (b + a)/2;
        if( (m*m - A) * (a*a - A) < 0 )
            b = m;
        else 
            a = m;
    }
    return m;
}
```

### v2
```
//牛顿法
double Sqrt(double x) 
{
    if (x == 0) 
        return 0;
    double res = 1, pre = 0;
    while (abs(res - pre) > 1e-6) 
    {
        pre = res;
        res = (res + x / res) / 2;
    }
    return int(res);
}
```
