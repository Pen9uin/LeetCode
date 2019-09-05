### v1
```
int power(int x, unsigned int n)
{
    if (n == 0)
        return 1;
    else if (n == 1)
        return x;
    else 
    {
        if (n % 2 == 1)
            return power(x, n / 2) * power2(x, n / 2) * x;
        else
            return power(x, n / 2) * power2(x, n / 2);
    }
}
```

### v2
```
int power(int x, unsigned int n)
{
    if (n == 0)
        return 1;
    int result = 1;
    while (n != 0)
    {
        if (n & 1)
            result *= x;
        x *= x;
        n >>= 1;
    }
    return result;
}
```
