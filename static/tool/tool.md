

#### 数字转货币格式 将100000转为100,000形式*/
```
export const commas = function (val) {
     return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
}
```

#### 保留两位小数并且整数部分三位一个逗号分隔符的数字金钱标准表示法：/*将100000转为100,000.00形式*/
```
export const dealNumber = function (money) {
    if (money && money != null) {
        money = String(money);
        var left = money.split('.')[0], right = money.split('.')[1];
        right = right ? (right.length >= 2 ? '.' + right.substr(0, 2) : '.' + right + '0') : '.00';
        var temp = left.split('').reverse().join('').match(/(\d{1,3})/g);
        return (Number(money) < 0 ? "-" : "") + temp.join(',').split('').reverse().join('') + right;
    } else if (money === null || money === undefined){
        return '- - -'
    } else {
        return '0.00';
    }
};
```
####  /*将100,000.00转为100000.00形式*/
```
export const undoNubmer = function (money) {
    if (money && money != null) {
        money = String(money);
        var group = money.split('.');
        var left = group[0].split(',').join('');
        return Number(left + "." + group[1]);
    } else {
        return "";
    }
}
```