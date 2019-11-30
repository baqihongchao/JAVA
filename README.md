

//声明单元方法:处理用户登录
@RequestMapping("userLogin")
public String userLogin(String loginname, String pwd, HttpSession session){
    //处理请求
    User user = userServiceImpl.selUserLoginService(loginname, pwd);
    //响应结果
        if(user!=null){
            //将用户信息存储到session对象中
            session.setAttribute("user",user);
            //重定向到主页面
            return "redirect:/main/main.jsp";//main.jsp在web下的main包里  redirect重定向
        }else{
            //增加登录失败标记
            session.setAttribute("flag","loginFail");
            //重定向到登录页面
            return "redirect:/login.jsp";//login.jsp在web下
        }
}
