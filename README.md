# Intrusion-detection
1. Giới thiệu
  
  Vấn đề bảo mật hiện đang trở thành mục tiêu lợi dụng của những kẻ tấn công, xâm nhập trái phép nhằm thực hiện những mưu đồ xấu, đe dọa tới tính an toàn về bảo mật thông tin của các tổ chức hay những người dùng kết nối mạng. Mặc dù, mỗi hệ thống máy tính đều có những cơ chế tự bảo vệ riêng nhưng có thể chưa đủ để phát hiện hay ngăn chặn những cuộc tấn công ngày một tinh vi hơn. 
  
  Vấn đề đặt ra là làm sao xây dựng được một hệ thống có thể phát hiện sớm và có hiệu quả các cuộc tấn công hay xâm nhập trái phép từ đó đưa ra những cảnh báo và biện pháp xử lý kịp thời. Những hệ thống phát hiện xâm nhập mạng đã được xây dựng vẫn chưa đủ linh hoạt, khả năng mở rộng không cao, cũng như không đủ mạnh để đối phó với các cuộc tấn công nói trên. Một vài nghiên cứu gần đây đưa ra một hướng tiếp cận mới dựa vào học máy cho bài toán phát hiện xâm nhập mạng.
  
  Thực nghiệm này chỉ nhằm mục đich học tập và nghiên cứu. Tôi sẽ dùng kiến thức về học máy và học sâu để đưa bài toán về bài toán phân loại nhị phân để giải quyết. Với hướng xử lí đa nhãn, tôi vẫn chưa thể thực nghiệm được do gặp vấn đề trong mất cân bằng phân bố nhãn.

2. Phương pháp

  Phần thực nghiệm được thực thi trên Colab.
  
  Độ đo: độ chính xác, f1-score và ma trận nhầm lẫn.
  
  Lựa chọn thuộc tính: WEKA, sử dụng CFS + Best First Search. Từ 41 thuộc tính -> 19 thuộc tính, chưa tính nhãn kết nối.
  
  Phương pháp: LSTM và một số thuật toán khác (Random Forest, Logistic Regression, Bernoulli Naive Bayes và SVM).
  
3. Dữ liệu

  NLS-KDD được sử dụng trong thực nghiệm này. Nó là bộ dữ liệu được cải thiện từ KDD1999 (được tạo cho thử thách KDD Cup vào năm 1999). Tuy nhiên, một vài vấn đề nghiêm trọng gây ảnh hưởng đến kết quả nghiên cứu được tìm thấy trong bộ dữ liệu KDD 1999 vào năm 2009. Cụ thể, một số lượng lớn các bản ghi dư thừa (78% trong dữ liệu đào tạo và 75% trong dữ liệu kiểm tra) được tìm thấy gây ra sự sai lệch. Ngoài ra, khi chọn ngẫu nhiên các tập hợp con của dữ liệu đào tạo và kiểm tra, kết quả thu về thường có thể đạt được độ chính xác phi thực tế rất cao. Do vậy, NSL-KDD được tạo ra. Nó bao gồm các bản ghi đã chọn của tập dữ liệu KDD 1999 hoàn chỉnh và không gặp phải những thiếu sót nói trên.
  
  NSL-KDD gồm 41 thuộc tính chưa kể nhãn của kết nối (kết nối bình thường hoặc tên một loại tấn công cụ thể), phần dữ liệu cho huấn luyện  gồm 125.973 bản ghi và tập dữ liệu kiểm tra gồm 22.544 bản ghi.
  
4. Chú thích

  Tôi thực nghiệm theo 2 hướng:
  
    - Không thực hiện lựa chọn thuộc tính (41 thuộc tính): Not_CFS_Intrusion_Detection
    
    - Có thực hiện lựa chọn thuộc tính (19 thuộc tính): CFS_Intrusion_Detection_Basic_models (thực nghiệm trên một số thuật toán khác), CFS_Intrusion_Detection_RNN_LSTM1_5 và CFS_Intrusion_Detection_RNN_LSTM2_3_4_99.4
    
5. Tham khảo

[1]UNB, “NSL-KDD dataset,” [Trực tuyến]. Available: https://www.unb.ca/cic/datasets/nsl.html. [Đã truy cập 06 2022].
