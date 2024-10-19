---
title: 期货合约的定价机制 - 以LME铜为例
date: 2024-09-09 23:30:31
mathjax: false
categories:
- Reading-Note
tags:
- Finacial 101
ShowToc: true
---

# 期货合约的定价机制 - 以LME铜为例

### Background 

- 大宗商品市场
  - 大宗商品主要交易场所
    - CME：芝加哥商品交易所
    - LEM：伦敦金属交易所
    - ICE
  - 大宗商品交易目的：
    - 国际**贸易**
    - **对冲**风险
    - **投机**与投资
- 市场分类：
  - 现金市场
  - 衍生品市场：
    - 期货 Future （场内交易）
    - 远期 Forward  （场外交易 OTC）
    - 掉期 Swaps 
    - 期权 Options 



### LME 铜的价格发现

- LME参考价格
  - 伦敦金属交易所铜的官方价格每日根据第二天早盘收盘时（伦敦时间 12:30-12:35，伦敦金属交易所公开喊价交易大厅）的买入价和卖出价确定。<u>**伦敦金属交易所官方结算价也是在场内确定的，是铜的现金卖方价格，广泛应用于世界各地的实物铜合约。**</u>这意味着它代表了任何经批准的伦敦金属交易所铜品牌的价格，这些铜可在两个工作日内交付于伦敦金属交易所全球仓库网络的任何地点。价格确定后，伦敦金属交易所会记录、分发和公布价格给世界各地的供应商，供应商再将数据传播给整个价值链上的行业用户。
  - 交易所视频 -> https://www.youtube.com/watch?v=Mic1Q0oVfgM&t=4s
- 溢价 (Premium) 与折扣 (discount)
  - LME参考价格不一定是最终合约价格。公司可以从这些价格发现组织和机制提供的更高透明度中受益。因此，公司可以更好地集中精力协商基础金属和其特定产品之间的溢价或折扣价值。**<u>这些溢价或折扣可能基于多种因素，其中包括最常提到的一些因素：地理位置、材料等级、杂质和交货条款。</u>**



### Future

- Future is a contract that is defined and traded in the exchange. The product is **obligation to buy/sell a standard quantity on a set future date, at a fixed price**.

  

### Long / Short Position

- Futrue contract are traded at future exchanges. The buyer of a future contract is said to be the **long** (多头) position holder, and the seller is said to be the **short** (空头) position holder.



### Physical delivery / Cash settlement

- Cash settlement is made based on the underlying reference rate. The parties settle by paying/receiving the loss/gain related to contract in cash when contract expires.



### Explain concepts with Example

*I'm growing Potatos at Diddly Squat Farm*

- **Future Contract:**
  - A standarlised legal agreement to buy or sell a financial asset ata predetermined price at a specified time in the future.
  - I don't know the market price in the coming year. Therefore, I want to set 100t potatos at price 100$/t in the next year, on 1st May 2025, to give me a garauntee profit.

- **Future exchange:**
  - Futrue contract are traded at future exchanges. The buyer of a future contract is said to be the **long** position holder, and the seller is said to be the **short** position holder.
