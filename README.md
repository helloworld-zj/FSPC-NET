# FSPC-NET

欢迎访问本仓库！本仓库旨在公开论文FSPC-NET: FREQUENCY-DOMAIN STYLE PERTURBATION AND PIXEL-LEVEL CONTRASTIVE LEARNING FOR DOMAIN-GENERALIZED MEDICAL IMAGESEGMENTATION中的代码实现及相关补充实验结果。


## 参数敏感性分析补充实验

为了回应审稿意见，我们进行了参数敏感性分析，具体实验内容包括：

- **实验目的**：评估模型对关键参数γ, α, and τ的稳定性和敏感程度。  
- **实验方法**：逐一调整参数值，记录模型性能变化。
- **实验数据**：Fundus眼底四个领域的数据。  

**1.在领域1上：**
<img width="1500" height="500" alt="myplot11" src="https://github.com/user-attachments/assets/cc9b64f0-7be8-4674-9be2-66cd1b97aa46" />

**2.在领域2上：**
<img width="1500" height="500" alt="myplot2" src="https://github.com/user-attachments/assets/1617d3a2-aea8-4988-818d-6a696b8eaaa2" />
**3.在领域3上：**
<img width="1500" height="500" alt="myplot3" src="https://github.com/user-attachments/assets/4e2ca473-3fca-491a-b569-4eff6f0ec2c3" />
**4.在领域4上：**
<img width="1500" height="500" alt="myplot4" src="https://github.com/user-attachments/assets/01906785-d073-470a-a37e-a99be85f5620" />

- **分析结论**：  
1.γ=0.9的选择是默认选择且合理的，实现了域间一致性最大化，在四个域上取得了平衡最佳的性能
  
2.各域对风格扰动的偏好差异显著，α=0.5时实现了最佳的平均性能和可接受的域间差异

3.各域对τ的敏感性相对较低，τ=0.07是鲁棒的选择，证明了对比学习框架的温度参数具有较好的鲁棒性

  敏感性分析验证了当前参数选择在多中心场景下的有效性，多中心域泛化需要在各域性能之间做出权衡，而非追求单一域的最优，为未来在更多医疗中心部署提供了参数调节的参考策略。
