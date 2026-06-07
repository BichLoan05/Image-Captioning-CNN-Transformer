# Image Captioning (From Scratch): Custom CNN + Transformer Decoder

Dự án xây dựng một hệ thống tự động sinh chú thích ảnh (Image Captioning) trên tập dữ liệu MS COCO. Điểm đặc biệt của dự án là tuân thủ yêu cầu xây dựng kiến trúc từ đầu (from scratch), bao gồm việc tự thiết kế mạng Custom CNN trích xuất đặc trưng và mạng Transformer Decoder giải mã văn bản, hoàn toàn không sử dụng các trọng số Pre-trained (như ResNet, VGG hay BERT).
## Kiến trúc Mô hình
* **Encoder:** Custom CNN (4 Convolutional Blocks) giữ nguyên bản đồ đặc trưng không gian (14x14) thay vì nén phẳng (Global Average Pooling), nhằm hỗ trợ tốt nhất cho cơ chế Attention.
* **Decoder:** Transformer Decoder áp dụng Masked Self-Attention và Multi-Head Cross-Attention để liên kết ngữ nghĩa giữa văn bản và tọa độ pixel.

## Kết quả Thực nghiệm & Phân tích
*Do giới hạn về tài nguyên tính toán (chạy trên Google Colab) và yêu cầu train từ đầu thay vì Fine-tuning, mô hình mới chỉ dừng ở mức hội tụ cơ bản.*

* **BLEU-1:** ~31.5% (Mô hình đã bắt đầu nhận diện đúng các thực thể và hình khối cơ bản trong ảnh).
* **BLEU-4:** ~6.0% (Mô hình học được các cụm cú pháp ngữ pháp tiếng Anh cốt lõi).
* **ROUGE-L:** ~31.7% (Bảo toàn ý nghĩa tổng thể khá cân bằng, không bị lặp từ quá nhiều).

## Hướng Phát Triển Tương Lai
1. Triển khai Beam Search thay cho Greedy Search trong giai đoạn Inference.
2. Huấn luyện thêm Epochs và áp dụng Learning Rate Scheduler.
3. Trực quan hóa Attention Heatmap trên ảnh đầu vào.
4. So sánh với các mô hình sử dụng Encoder Pre-trained như ResNet hoặc EfficientNet.
