# Tổng quan
CMake build for the B-Tree library from hydrus.org.uk

### Để biên dịch các công cụ đi kèm với thư viện B-Tree
Cần bật tùy chỉnh ORIGINAL_EXECUTABLE=ON,
ví dụ có thể sử dụng lệnh: 

`cmake ../ -DORIGINAL_EXECUTABLE=ON`

Lý do không biên dịch các công cụ này ở chế độ mặc định: Vì mục đính sử dụng chính của mã nguồn này được cho là để hỗ trợ tích hợp thư viện B-Tree vào một ứng dụng khác được tạo bằng CMake

-----------------------------------------------------------------------------------
# Các lệnh cơ bản của B tree

`int btinit(void)`
    
    Khởi tạo thư viện B tree

`BTA *btcrt(char* fid, int nkeys, int shared)   //Tạo file B tree`
 ```  
    fid: tên file
    nkeys: số lượng khóa nhiều nhất
    shared: nếu bằng 0 thì cho phép share, nếu khác 0 thì không cho phép hàm sẽ trả về root, nếu thất bại sẽ trả về NULL
```

`BTA *btopn(char *fid,int mode,int shared);    //Mở B tree file`
```
    fid: tên file
    mode: bằng 0 cho phép update, khác 0 thì ko cho phép
    shared: 0 sẽ không cho phép access, khác 0 sẽ cho phép trả về NULL hoặc con trỏ root
```

`int btcls(BTA *btact);    //Thoát B tree file`
```
    đóng file B tree trỏ bởi con trỏ btact, nếu thành công sẽ trả về gía trị 0, khác 0 thì đã có lỗi xảy ra
```

`int btins(BTA *btact, char *key, char *data, int dsize);    //Chèn key và data vào B tree`
```
    trả về 0 nếu thành công;
    dsize: độ dài của data
```

`int btupd(BTA *btact, char *key, char *data, int dsize);    //update data cho key`

`int btsel(BTA *btact, char *key, char *data, int dsize, int *rsize);   //xác định dữ liệu của khóa có sẵn`
```
    trả lại data record của key tồn tại
```

`int btdel(BTA *btact, char *key);    //Xóa key và data`
```
    trả về 0 nếu thành công
```

`int btrecs(BTA *btact, char *key, int *rsize);      //Xác định kích cỡ của data`
