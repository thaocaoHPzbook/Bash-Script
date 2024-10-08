# 1) Cấu trúc file bash
Dòng đầu tiên và bắt buộc với một file bash với đuôi mở rộng là .sh ( trên Linux ) hoặc .bat trên Window ) là câu lệnh này

    #!/bin/bash
    // tiếp theo là những câu lệnh thực thi

VD : myscript.sh

    #!/bin/bash   
    echo Hello  
    // in ra màn hình terminal chứ Hello`

Để run file này đơn giản trên màn hình terminal chỉ cần chạy **./myscript.sh**

# 2) Các biến trong file bash
Có 2 kiểu biến trong file bash
- Setting a value for a variable.
- Reading the value for a variable.

Đơn giản khi chúng ta cần tham chiếu và để đọc giá trị của biên đó thì ta dùng Reading the value với cú pháp thêm dấu $ trước tên biến Khi chúng ta muốn gán giá trị cho biến thì ta dùng Setting a value chỉ cần bỏ dấu $ đằng trước đi là được

Một số biến của hệ thống như :

    $0- Tên của file  Bash script.  
    $1 - $9 - lần lượt là các đối số truyền vào cho file Bash script.  
    $# - Số lượng các  arguments chúng ta truyền vào cho file the Bash script.  
    $@ - Tất cả các đối số cung cấp cho file  Bash script.  
    $? - Trạng thái của câu lệnh thực hiện gần nhất ( 0 -> true , 1 -> false )   
    $$ - ID của script hiện tại.

VD :

    #!/bin/bash
    arg=$1
    echo arguments1 = $arg

Run file : **./myscript.sh 123** với 123 là giá trị argument truyền vào

màn hình sẽ in ra kết quả như sau :

    nambd@nambd-HP:~/Desktop$ bash ./myscipt.sh  123
    arguments1 = 123

# 3) Input trong file bash

Như ví dụ bên trên mình đang truyển giá trị theo kiểu Command line arguments

Một cách khác là mình sẽ dùng cách Ask the User for Input

Cú pháp :

    read value

VD :

    nambd@nambd-HP:~/Desktop$ bash ./myscipt.sh 
    Enter your name :
    Hihi 
    Your name is Hihi

Một số option

-p : thêm dấu nhắc nhập lệnh -s : ẩn đi giá trị bạn nhập

    #!/bin/bash
    read -p 'Username: ' uservar
    read -sp 'Password: ' passvar 
    echo Username : $uservar Password : $passvar

Khi bạn muốn nhập nhiều giá trị :

    read var1 var2 var3

# 4) If , If else Statements

Cậu lệnh điều kiện

Cú pháp

    if [ <some test> ]
    then
    <commands>
    else
    <other commands>
    fi

VD :

    #!/bin/bash
    
    if [ $# -eq 1 ] // kiêm tra số lượng các argument 
    then
    nl $1
    else
    //some action 
    fi

Hoặc câu lệnh elif

    if [ <some test> ]
    then
    <commands>
    elif [ <some test> ] 
    then
    <different commands>
    else
    <other commands>
    fi

VD :

    #!/bin/bash
    
    if [ $1 -ge 18 ]
    then
    echo You may go to the party.
    elif [ $2 == 'yes' ]
    then
    echo You may go to the party but be back before midnight.
    else
    echo You may not go to the party.
    fi

Boolean Operations gồm có

- and - &&
- or - ||

VD

    if [ -r $1 ] && [ -s $1 ]
    then
    echo This file is useful.
    fi

5) Case Statements

Cú pháp :

    case <variable> in
    <pattern 1>)
    <commands>
    ;;
    <pattern 2>)
    <other commands>
    ;;
    esac

VD :
    
    #!/bin/bash
    case $1 in
    start)
    echo starting
    ;;
    stop)
    echo stoping
    ;;
    restart)
    echo restarting
    ;;
    *)
    echo don't know
    ;;# Bash-Script
