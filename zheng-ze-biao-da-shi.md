# 正则表达式

---

陆续会更新

```java
 /**
     * 校验手机号码
     * @param mobile
     * @return
     */
    public static final boolean isMoblie(String mobile){
        boolean flag = false;
        if (null != mobile && !mobile.trim().equals("") && mobile.trim().length() == 11) {
            Pattern pattern = Pattern.compile(REGEX_PHONE);
            Matcher matcher = pattern.matcher(mobile.trim());
            flag = matcher.matches();
        }
        return flag;
    }

    /**
     * 校验邮箱
     * @param value
     * @return
     */
    public static final boolean isEmail(String value){
        boolean flag = false;
        if (null != value && !value.trim().equals("")) {
            Pattern pattern = Pattern.compile(REGEX_EMAIL);
            Matcher matcher = pattern.matcher(value.trim());
            flag = matcher.matches();
        }
        return flag;
    }

    /**
     * 校验密码
     * @param password
     * @return 长度符合返回true，否则为false
     * @since 2015-09-24
     */
    public static final boolean isPassword(String password){
        boolean flag = false;
        if (null != password && !password.trim().equals("")) {
            password = password.trim();
            if(password.length() >= 6 && password.length() <= 20){
                return true;
            }
        }
        return flag;
    }

    /**
     * 正则表达式校验,符合返回True
     * @param regex 正则表达式
     * @param content 校验的内容
     * @return
     */
    public static boolean isMatch(String regex, CharSequence content){
        return Pattern.matches(regex, content);
    }

    /**
     * 大写字母
     * @param str
     * @return
     */
    public static boolean isUpperCase(String str){
        if(TextUtils.isEmpty(str)){
            return false;
        }
        String reg = "^[A-Z]$";
        return isMatch(reg,str);
    }

    /**
     * 身份证号
     * @param value
     * @return
     */
    public static boolean isIdNumber(String value){
        boolean flag = false;
        if (null != value && !value.trim().equals("")) {
            Pattern pattern = Pattern.compile(REGEX_ID);
            Matcher matcher = pattern.matcher(value.trim());
            flag = matcher.matches();
        }
        return flag;
    }
```



