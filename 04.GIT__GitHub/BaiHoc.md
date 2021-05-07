# BẮT ĐẦU
1. Kiểm tra đã thêm tài khoản vào chưa?
    - Systax : git config --list
    - Nếu chưa có user.name và user.password thì chưa có gì cả cần thêm tài khoản
2. Set Tài khoản
    - Systax:
        + Set username :
            $ git config --global user.username hieuemmm
            Kết quả => Không có báo lỗi gì là ok
            + Kiểm tra username tên là gì ?
                $ git config user.username
                Kết quả => hieuemmm
        + Set email :
            $ git config --global user.email hieus247@gmail.com
            Kết quả => Không có báo lỗi gì là ok
            + Kiểm tra email tên là gì ?
                $ git config user.email
                Kết quả => hieus247@gmail.com
        + Set password :
            $ git config --global user.password 01658692160
            Kết quả => Không có báo lỗi gì là ok
            + Kiểm tra password tên là gì ?
                $ git config user.password
                Kết quả => 01658692160
    - NOTE :
        + Global là chế độ mọi người sẽ biết chúng ta là ai.
        + username là tên giả của bạn đặt gì thì đặt
        + email là gmail của bạn
        + password là mật khẩu email của bạn
        - Kiểm tra lại bằng lênh :(
            Administrator@HieuEM MINGW64 ~/Desktop
            $ git config --list
            diff.astextplain.textconv=astextplain
            filter.lfs.clean=git-lfs clean -- %f
            filter.lfs.smudge=git-lfs smudge -- %f
            filter.lfs.process=git-lfs filter-process
            filter.lfs.required=true
            http.sslbackend=openssl
            http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
            core.autocrlf=true
            core.fscache=true
            core.symlinks=false
            pull.rebase=false
            credential.helper=manager-core
            credential.https://dev.azure.com.usehttppath=true
            init.defaultbranch=master
            user.username=hieuemmm
            user.email=hieus247@gmail.com
            user.password=01658692160
        )
3. Remove Tài khoản
    $  git config --global --unset user.username
    $  git config --global --unset user.password
    $  git config --global --unset user.email
# LỆNH CƠ BẢN
1. Trang thái của một files
    - Untracked (Chưa được theo dõi)
        + Chưa có commit 
    - Tracked (đã được theo dõi)
        + Modified (được sửa đổi) 
        + UnModified (chưa được sửa đổi cả) 
        + Staged (Sửa xong và được add nó)
    - Khi clone về thì tất cả các file ở trạng thái UnModifier
    - Khi xóa một file nào đó đi thì file đó trở về trạng thái Untracked (Không theo dõi nữa)
    - Các file không xóa mà sửa đổi (Thêm, bớt code) thì sẽ trở thành trạng thái Modified
    - Khi một file ở trạn thái Modified được add thì sẽ trở thành trạng thái Staged (đánh chỉ số cho nó)
    - Khi một file ở trạng thái Staged mà được commit thì sẽ trở về trạng thái UnModified
2. Git Clone (Lấy bản sao về):
    + Cần tạo ra thư mục để chứa dữ liệu khi clone về máy chúng ta
    + Tại ngay trong thư mục đó mở Git lên
    - Systax:
        git clone URL
    - Khi clone xong nó sẽ báo "100% n/n. Done."
    - Systax clone vể và đổi tên repository luôn
        git clone URL [Tên repository]
    - Khi clone xong nó sẽ báo "100% n/n. Done."
    - NOTE :
        repository là kho chứa
3. Git pull
    Tác dụng => Đồng bộ code từ trên githb về máy
4. Git init
    Tác dụng => Tạo file .git đặt vào bên trong thư mục muốn theo dõi sự thay đổi 
5. Git status
    - Dùng để xem trạng thái của 1 file 
    - Nếu "Untracked file:..."
        Thì đây là danh sách file chưa được theo dõi, cần add vào 
    - Nếu "nothing to commit, working tree clean"( không có gì để commit, cây công việc đang sạch sẽ)
        => Nghĩa là tất cả các file đang ở trạng thái UnModified - Chưa có file nào được sửa đổi
    - Nếu hiển thị màu đỏ thì file đó đang ở trạng thái Modified (đã có sự thay đổi bên trong code)
    - Nếu file đó có màu Xanh tứ là đang ở trạng thái Stage 
        + Màu này sinh ra bởi vì Modified đã được add nên chuyển sang trạng thái Stage 
    - Nếu tất cả các file đang ở trạng thái Stage mà commit thì sẽ chuyển tất cả về trạng thái UnModified

    - ADD là gì? 
        Là chuẩn bị sẵn sàng cho lần commit sắp tới (giống như chụp màn hình tất cả để ghi vào lịch sử)
    - COMMIT là gì?
        Là xác nhận chính thức rằng chúng ta sẽ lưu lại 1 bản sao/ trạng  thái của các file đã được add (đánh chỉ số)
6. Git add
    - Systax:
        git add .  : Stage all (new, modified, deleted) files trong thư mục hiện tại
        git add -A : Stage all (new, modified, deleted) files
        git add -u : Stage modified and deleted files trong lần commit trước, không quan tâm files mới
7. Git commit
    - Tác dụng : Để xác minh rằng chúng ta thực hiện thay đổi này
    Sau khi add files đã chuẩn bị commit rồi, cần commit lên (Bắt buộc phải add trước khi commit mới commit được) 
    git commit -m "Nội dung mô tả (nên đặt nội dung thay đổi lới nhất trong này)"
    git commit -a -m "Nội dung mô tả"
        => vừa add tất cả vừa commit luôn 1 lần 
    - Git commit --amend
        - Tác dụng : Gộp commit này và commit trước đó lại làm 1, chứ không phải tạo ra một commit mới
        - Lưu ý : Mã commit trước đó sẽ bi thay đổi
        - Sau đó sửa Mess của commit
        - Rồi Ctrl + X (Exit)=> Y (yes)
8. Git Push
    Tác dụng => Đồng bộ code từ máy lên github
    - Yêu cầu:
        + Đã tạo repository trên github
    - Đầu tiên :
        + Tạo theo dõi git init
    - S2:
        + Sau khi đã add > rồi commit xong xuôi
    - S3: gõ lệnh
        + git push -u origin master
    - S5:
        Chờ đợi.
        Sau đó git yêu cầu chúng ta nhập Username và Password
    - Hoàn thành.
9. Git Log
    Hoặc git log --oneline => xem tổng quat commit trên 1 dòng
    Hoặc git log -3 => xem 3 commit gần nhất
    Hoặc git log -p => Xem chi tiết từng commit
        + Nhánh nào là nhánh Master
        + Mã commit
        + Thời gian commit 
        + Ghi chú của commit
    - Thoát xem lịch sử : Nhấn phim "Q"
    - NOTE:
        + Lịch sử viết từ trên dưới lên trên
10. Git reset:
    - Tác dụng : Đưa con trỏ HEAD về một commit cụ thể nào đó 
    - Đầu tiên mở git log để xem danh sách commit
        + Để lấy mã commit
    - Có hai loại Git Reset :
        + Bình thường : Quay lại và vẫn giũ các commit đằng sau
        + hard : Mất hết commit đằng sau [commit muốn quay lại], rất nguy hiểm
    - Systax:
        git reset [mã commit]
        git reset --hard [mã commit]
11. Git checkout [mã commit]
    - Dùng để checkout về commit để xem thử file
12. Git reset HEAD [tên file cần loại bỏ]
    - Tác dụng: 
        + Sau khi add xong, nhưng muốn loại bỏ các file không mong muốn 
        + Để chuẩn bị cho lần commit sắp tới
# NHÁNH (NÂNG CAO)
1. Git branch
    Tác dụng => để xem danh sách nhánh
2. Git branch nhanh_1
    Tác dụng => Tạo ra một nhánh tên là nhanh_1
3. Di chuyển cussor sang nhánh khác
    git checkout branch_1
    Tác dụng => Chuyển cussor về nhánh branch_1
4. Đổi tên nhánh
    TA CÓ:
        $ git branch
        * branch_1
        branch_2
        branch_3
        master
    Lưu ý: Không đổi tên nhánh master được.
    - Có 2 ngử cảnh đổi tên:
        + Đang đứng nhánh A và muốn đổi tên nhánh A:
            git branch -m branch_1_rename
        + Đang đứng nhánh A và muốn đổi tên nhánh B:
            git branch -m branch_2 branch_2_rename
5. Vừa tạo nhánh vừa di chuyển cussor sang đó:
    git checkout -b branch_4
    Tác dụng => Vừa tạo ra nhánh branch_4 vừa Switch cussor sang đó