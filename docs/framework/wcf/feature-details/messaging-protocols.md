---
title: 訊息通訊協定
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: c900c8fde8b13b4766fb245de2bab46b5601f135
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="messaging-protocols"></a>訊息通訊協定
Windows Communication Foundation (WCF) 通道堆疊利用編碼和傳輸通道內部訊息表示法轉換為其 wire 格式，並將其傳送使用特定的傳輸。 最常用於 Web 服務互通性的傳輸為 HTTP，而 Web 服務最常用的編碼為 XML 架構的 SOAP 1.1、SOAP 1.2 和訊息傳輸最佳化機制 (MTOM)。  
  
 本主題涵蓋下列通訊協定所採用的 WCF 實作細節<xref:System.ServiceModel.Channels.HttpTransportBindingElement>。  
  
|規格/文件|連結|  
|-----------------------------|----------|  
|HTTP 1.1|http://www.ietf.org/rfc/rfc2616.txt|  
|SOAP 1.1 HTTP 繫結|http://www.w3.org/TR/2000/NOTE-SOAP-20000508/第 7 節|  
|SOAP 1.2 HTTP 繫結|http://www.w3.org/TR/soap12-part2/第 7 節|  
  
 本主題涵蓋 WCF 實作詳細資料，下列通訊協定，<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>和<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>採用。  
  
|規格/文件|連結|  
|-----------------------------|----------|  
|XML|http://www.w3.org/TR/REC-xml|  
|SOAP 1.1|http://www.w3.org/TR/2000/NOTE-SOAP-20000508/|  
|SOAP 1.2 核心|http://www.w3.org/TR/soap12-part1/|  
|WS-Addressing 2004/08|http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/|  
|W3C Web 服務定址 1.0 - 核心|http://www.w3.org/TR/2006/REC-ws-addr-core-20060509|  
|W3C Web 服務定址 1.0 - SOAP 繫結|http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509|  
|W3C Web 服務定址 1.0 - WSDL 繫結|http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/|  
W3C Web 服務定址 1.0 - 中繼資料|http://www.w3.org/TR/ws-addr-metadata/|  
|WSDL SOAP1.1 繫結|http://www.w3.org/TR/wsdl/|  
|WSDL SOAP1.2 繫結|http://www.w3.org/Submission/wsdl11soap12/|  
  
 本主題涵蓋 WCF 實作詳細資料，下列通訊協定，<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>採用。  
  
|規格/文件|連結|  
|-----------------------------|----------|  
|XOP|http://www.w3.org/TR/xop10/|  
|MTOM + SOAP 1.2 繫結|http://www.w3.org/TR/soap12-mtom/|  
|MTOM SOAP 1.1 繫結|http://www.w3.org/Submission/soap11mtom10/|  
|MTOM WS-Policy 判斷提示|http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.|  
  
 下列 XML 命名空間與關聯的前置詞會在本主題中使用。  
  
|前置詞|命名空間統一資源識別元 (URI)|  
|------------|---------------------------------------------------|  
|s11|http://schemas.xmlsoap.org/soap/envelope|  
|s12|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://www.w3.org/2004/08/addressing|  
|wsam|http://www.w3.org/2007/05/addressing/metadata|  
|wsap|http://schemas.xmlsoap.org/ws/2004/09/policy/addressing|  
|wsa10|http://www.w3.org/2005/08/addressing|  
|wsaw10|http://www.w3.org/2006/05/addressing/wsdl|  
|xop|http://www.w3.org/2004/08/xop/include|  
|xmime|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
dp|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="soap-11-and-soap-12"></a>SOAP 1.1 和 SOAP 1.2  
  
### <a name="envelope-and-processing-model"></a>封套和處理模型  
 WCF 實作 SOAP 1.1 封套，以處理下列 Basic Profile 1.1 (BP11) 和 Basic Profile 1.0 (SSBP10)。 SOAP 1.2 封套處理實作了下列 SOAP12-Part1。  
  
 本節說明對於 BP11 和 SOAP12 Part1 WCF 所採取的某些實作選項。  
  
#### <a name="mandatory-header-processing"></a>強制處理標頭  
 WCF 會遵循規則處理標頭標記為`mustUnderstand`SOAP 1.1 和 SOAP 1.2 規格中，具有下列變化中所述。  
  
 輸入 WCF 通道堆疊的訊息是由個別的通道相關聯的繫結項目，例如設定、 文字訊息編碼、 安全性、 可靠傳訊和交易處理。 每個通道都會從關聯的命名空間辨識標頭，並將其標記為已辨識。 一旦訊息進入發送器，作業格式器便會讀取對應之訊息/作業合約所需的標頭，並將其標記為已辨識。 接著發送器便會檢查是否有任何剩餘之未辨識，但標記為 `mustUnderstand` 的標頭，並擲回例外狀況。 包含 `mustUnderstand` 標頭的訊息會以尚未由收件者應用程式碼處理的收件者為目標。  
  
 此類分層式處理可將 SOAP 節點的基礎結構層與應用程式層分割：  
  
-   B1111： 無法辨識的標頭會偵測到由 WCF 基礎結構通道堆疊中，處理訊息之後，但它由應用程式處理之前  
  
     SOAP 1.1 和 SOAP 1.2 之間的 `mustUnderstand` 標頭值不同。 Basic Profile 1.1 要求 SOAP 1.1 訊息的 `mustUnderstand` 值必須為 0 或 1。 SOAP 1.2 允許 0、1、`false` 和 `true` 等值，但建議發出 `xs:boolean` 值的標準表示 (`false`、`true`)。  
  
-   B1112: WCF 發出`mustUnderstand`值 0，1 表示 SOAP 1.1 和 SOAP 1.2 版的 SOAP 封套。 WCF 接受的整個值空間`xs:boolean`如`mustUnderstand`標頭 (0、 1、 `false`， `true`)  
  
#### <a name="soap-faults"></a>SOAP 錯誤  
 下列是 WCF 特定 SOAP 錯誤實作清單。  
  
-   B2121: WCF 會傳回下列 SOAP 1.1 錯誤代碼： `s11:mustUnderstand`， `s11:Client`，和`s11:Server`。  
  
-   B2122: WCF 會傳回下列 SOAP 1.2 錯誤碼： `s12:MustUnderstand`， `s12:Sender`，和`s12:Receiver`。  
  
### <a name="http-binding"></a>HTTP 繫結  
  
#### <a name="soap-11-http-binding"></a>SOAP 1.1 HTTP 繫結  
 WCF 實作 SOAP1.1 HTTP 繫結 Basic Profile 1.1 規格 3.4 節，以下列說明：  
  
-   B2211: WCF 服務未實作 HTTP POST 要求重新導向。  
  
-   B2212: WCF 用戶端支援 HTTP Cookie 3.4.8。  
  
#### <a name="soap-12-http-binding"></a>SOAP 1.2 HTTP 繫結  
 SOAP 1.2-2 (SOAP12Part2) 規格以下列說明所述，WCF 會實作 SOAP 1.2 HTTP 繫結。  
  
 SOAP 1.2 為 `application/soap+xml` 媒體類型引入了選擇性的動作參數。 這個參數對於最佳化訊息分派非常有用，不需要在未使用 WS-Addressing 的情況下剖析 SOAP 訊息的主體。  
  
-   R2221：在 SOAP 1.2 要求上呈現時，`application/soap+xml` 動作參數必須符合對應 WSDL 繫結內部之 `soapAction` 項目的 `wsoap12:operation` 屬性。  
  
-   R2222：在 SOAP 1.2 訊息上呈現時，若使用了 WS-Addressing 2004/08 或 WS-Addressing 1.0，則 `application/soap+xml` 動作參數必須符合 `wsa:Action`。  
  
 當 WS-Addressing 已停用，且傳入的要求未包含動作參數時，訊息 `Action` 會視為未指定。  
  
## <a name="ws-addressing"></a>WS-Addressing  
 WCF 實作 Ws-addressing 的 3 的版本：  
  
-   WS-Addressing 2004/08  
  
-   W3C Web 服務定址 1.0 核心 (ADDR10-CORE) 和 SOAP 繫結 (ADDR10-SOAP)  
  
-   WS-Addressing 1.0 - 中繼資料  
  
### <a name="endpoint-references"></a>端點參考  
 所有 WCF 實作的 Ws-addressing 版本來描述端點都使用了端點參考。  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a>端點參考和 WS-Addressing 版本  
 WCF 會實作一些使用 Ws-addressing 的基礎結構通訊協定，以及在特定`EndpointReference`項目和`W3C.WsAddressing.EndpointReferenceType`類別 （例如，Ws-reliablemessaging、 Ws-secureconversation 和 Ws-trust）。 WCF 還支援使用任一版本的 Ws-addressing 其他基礎結構通訊協定。 WCF 端點支援每個端點的 Ws-addressing 版本。  
  
 R3111 的命名空間`EndpointReference`項目或與 WCF 端點交換訊息中使用的類型必須符合的 WS 定址此端點實作版本。  
  
 例如，如果 WCF 端點實作了 Ws-reliablemessaging，`AcksTo`內此類端點所傳回的標頭`CreateSequenceResponse`會使用 Ws-addressing 的版本，`EncodingBinding`項目會指定此端點。  
  
#### <a name="endpoint-references-and-metadata"></a>端點參考和中繼資料  
 有許多案例都需要與中繼資料通訊，或需要參考指定之端點的中繼資料。  
  
 B3121: WCF 採用 Ws-metadataexchange (MEX) 規格第 6 節以傳值方式或傳址包含端點參考中繼資料中所述的機制。  
  
 假設 WCF 服務需要使用在權杖簽發者所發出的安全性判斷提示標記語言 (SAML) 權杖進行驗證的http://sts.fabrikam123.com。WCF 端點描述這項驗證需求使用`sp:IssuedToken`含有巢狀判斷提示`sp:Issuer`指向權杖簽發者的判斷提示。 存取 `sp:Issuer` 判斷提示的用戶端應用程式必須知道如何與權杖簽發者端點進行通訊。 用戶端需要知道與權杖簽發者有關的中繼資料。 使用 MEX 中定義的端點參考中繼資料延伸，WCF 會提供權杖簽發者中繼資料的參考。  
  
```xml  
<sp:IssuedToken>  
  <sp:Issuer>  
    <wsa10:Address>  
      http://sts.fabrikam123.com  
    </wsa10:Address>  
    <wsa10:Metadata>  
      <mex:Metadata>  
        <mex:MetadataSection>  
          <mex:MetadataReference>  
            <wsa10:Address>  
              http://sts.fabrikam123.com/mex  
            </wsa10:Address>  
          </mex:MetadataReference>  
        </mex:MetadataSection>  
      </mex:Metadata>  
    </wsa10:Metadata>  
  </sp:Issuer>  
</sp:IssuedToken>  
```  
  
### <a name="message-addressing-headers"></a>訊息定址標頭  
  
#### <a name="message-headers"></a>訊息標頭  
 這兩個 Ws-addressing 版本，WCF 會使用下列的訊息標頭如規格所規定`wsa:To`， `wsa:ReplyTo`， `wsa:Action`， `wsa:MessageID`，和`wsa:RelatesTo`。  
  
 B3211： 對於 Ws-addressing 的所有版本，WCF 會為準，但根據預設，Ws-addressing 訊息標頭不會產生`wsa:FaultTo`和`wsa:From`。  
  
 與 WCF 應用程式互動的應用程式可以將這些訊息標頭和 WCF 將會處理它們。  
  
#### <a name="reference-parameters-and-properties"></a>參考參數和屬性  
 WCF 實作端點參考參數和參考 p 的處理  
  
 屬性的處理。  
  
 B3221： 當設定為使用 Ws-addressing 2004/08，WCF 端點不會區分處理參考屬性和參考參數。  
  
### <a name="message-exchange-patterns"></a>訊息交換模式  
 包含在 Web 服務作業叫用的訊息順序稱為*訊息交換模式*。 WCF 支援單向、 要求-回覆和雙工訊息交換模式。 本章節將根據所使用的訊息交換模式，釐清訊息處理上的 WS-Addressing 需求。  
  
 在本章節中，要求者會傳送第一個訊息，而回應程式將會接收第一個訊息。  
  
#### <a name="one-way-message"></a>單向訊息  
 當 WCF 端點設定為支援訊息與給定`Action`採用單向模式時，WCF 端點便會遵循下列行為和需求。 除非另行指定，則行為和規則將套用這兩個版本的 Ws-addressing WCF 中支援：  
  
-   R3311：要求者必須加入由端點參考指定的 `wsa:To`、`wsa:Action` 和所有參考參數的標頭。 在使用了 WS-Addressing 2004/08，並且以端點參考指定 [reference properties] 時，也必須在訊息內加入對應的標頭。  
  
-   B3312：要求者可以加入 `MessageID`、`ReplyTo` 和 `FaultTo` 標頭。 接收者的基礎結構將會忽略它們，並且會將它們傳遞給應用程式。  
  
-   R3313：使用了 HTTP，而且沒有訊息在 HTTP 回應階段傳送時，回應程式必須傳送一個含有空主體的 HTTP 回應以及 HTTP 202 狀態碼。  
  
     當使用 HTTP 傳輸，而且作業合約宣告訊息為單向時，HTTP 回應仍舊可以用來傳送基礎結構訊息，例如，HTTP 回應上的可靠訊息可以傳送 `SequenceAcknowledgement` 訊息。  
  
-   B3314: WCF 回應程式不會在回應單向訊息傳送的錯誤訊息。  
  
#### <a name="request-reply"></a>要求-回覆  
 當 WCF 端點設定的訊息指定`Action`採用要求-回覆模式時，WCF 端點便會遵循行為和需求。 除非另行指定，則行為和規則將套用這兩個版本的 Ws-addressing WCF 中支援：  
  
-   R3321： 要求者必須在要求中包含`wsa:To`， `wsa:Action`， `wsa:MessageID`，和所有參考參數或參考屬性 （或兩者） 的端點參照所指定的標頭。  
  
-   R3322：使用 WS-Addressing 2004/08 時，`ReplyTo` 也必須包含在要求中。  
  
-   R3323： 使用 Ws-addressing 1.0 時和`ReplyTo`不存在於要求時，[address] 屬性等於預設端點參考 」http://www.w3.org/2005/08/addressing/anonymous"使用。  
  
-   R3324： 要求者必須加入`wsa:To`， `wsa:Action`，和`wsa:RelatesTo`在回覆訊息中的標頭，以及所有的參考參數或參考屬性 （或兩者） 所指定的標頭`ReplyTo`端點參考要求。  
  
### <a name="web-services-addressing-faults"></a>Web 服務定址錯誤  
 R3411: WCF 會產生下列由 Ws-addressing 2004/08 定義的錯誤。  
  
|程式碼|原因|  
|----------|-----------|  
|wsa:DestinationUnreachable|訊息到達時如帶有 `ReplyTo`，其回覆位址與為此通道所建立的不同。|  
|wsa:ActionNotSupported|與端點關聯的基礎結構通道或發送器，不會辨識 `Action` 標頭內指定的動作。|  
  
 R3412: WCF 會產生下列由 Ws-addressing 1.0 定義的錯誤。  
  
|程式碼|原因|  
|----------|-----------|  
|wsa10:InvalidAddressingHeader|重複的`wsa:To`， `wsa:ReplyTo`，`wsa:From`或`wsa:MessageID`。 重複的`wsa:RelatesTo`具有相同`RelationshipType`。|  
|wsa10:MessageAddressingHeaderRequired|所需的定址標頭遺失。|  
|wsa10:DestinationUnreachable|以 `ReplyTo` 到達的訊息，其回覆位址與為此通道所建立的不同。 而且沒有端點可在 To 標頭內指定的位址上進行接聽。|  
|wsa10:ActionNotSupported|在 `Action` 標頭內指定的動作，不會由基礎結構通道或與端點關聯的發送器進行辨識。|  
|wsa10:EndpointUnavailable|RM 通道會將此錯誤送回，指出端點將不會根據 `CreateSequence` 訊息之定址標頭檢查的順序進行處理。|  
  
 之前表格中的程式碼對應至 SOAP 1.1 內的 `FaultCode` 和 SOAP 1.2 內的 `SubCode` (使用 Code=Sender)。  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 繫結和 WS-Policy 判斷提示  
  
#### <a name="indicating-use-of-ws-addressing"></a>指出使用了 WS-Addressing  
 WCF 使用原則判斷提示來指出端點的 Ws-addressing 的特定版本的支援。  
  
 下列原則判斷提示具有端點原則主體 [WS-PA]，並指出必須使用 WS-Addressing 2004/08，從端點傳送及接收訊息。  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 此原則判斷提示擴大了 WS-Addressing 2004/08 規格。  
  
 下列原則判斷提示指出傳送/接收的訊息必須使用 WS-Addressing 1.0。  
  
```xml
<wsam:Addressing/>   
```  
  
 下列原則判斷提示具有端點原則主體 [WS-PA]，並指出必須使用 WS-Addressing 2004/08，從端點傳送及接收訊息。  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 `wsaw10:UsingAddressing` 項目是從 [WS-Addressing-WSDL] 借用的，並且在 WS-Policy 的內容中使用，以符合該規格第 3.1.2 節的規範。  
  
 使用定址不會改變 WSDL 1.1、SOAP 1.1 和 SOAP 1.2 HTTP 繫結的語意。 例如，若預期要回覆使用定址和 WSDL SOAP 1.x HTTP 繫結傳送至端點的要求，此回覆必須使用 HTTP 回應傳送。  
  
 若為透過 HTTP 回應傳送的回覆，WS-AM 判斷提示為：  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 完整的原則判斷提示看起來可能像這樣：  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 不過，有一些訊息交換模式可從要求者和回應程式之間所建立的兩個獨立反向 HTTP 連線中獲益，例如，由回應程式所傳送之未經要求的單向訊息。  
  
 WCF 提供的功能，這兩個基礎傳輸通道可用以構成複合雙工通道，其中一個通道用於輸入訊息，而其他則用於輸出訊息。 在使用 HTTP 傳輸的情況下，複合雙工提供了兩種反向的 HTTP 連線。 要求者會使用其中一個連線傳送訊息給回應程式，而回應程式則使用另一個連線將訊息傳回給要求者。  
  
 若為透過個別 HTTP 要求傳送的回覆，WS-AM 判斷提示為：  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 完整的原則判斷提示看起來可能像這樣：  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 下列具有端點原則主體 [WS-PA] 的判斷提示，在使用了 WSDL 1.1 SOAP 1.x HTTP 繫結的端點上使用時，會要求以個別的反向 HTTP 連線，將訊息在要求者和回應程式間傳送。  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 上一個陳述式會導致在要求訊息的 `wsa:ReplyTo` 標頭上，必須有以下需求：  
  
-   R3514： 要求傳送至端點的訊息必須要有`ReplyTo`具有標頭`[address]`屬性不等於"http://www.w3.org/2005/08/addressing/anonymous"如果端點使用 WSDL 1.1 SOAP 1.x HTTP 繫結，並有替代的原則`wsap10:UsingAddressing`或`wsap:UsingAddressing`判斷提示搭配`cdp:CompositeDuplex`附加。  
  
-   R3515： 要求傳送至端點的訊息必須要有`ReplyTo`具有標頭`[address]`屬性等於"http://www.w3.org/2005/08/addressing/anonymous"，或沒有`ReplyTo`all、 如果端點使用 WSDL 1.1 SOAP 1.x HTTP 繫結，並有原則替代的標頭與`wsap10:UsingAddressing`判斷提示，且沒有`cdp:CompositeDuplex`附加的判斷提示。  
  
-   R3516： 要求傳送至端點的訊息必須要有`ReplyTo`具有標頭`[address]`屬性等於"http://www.w3.org/2005/08/addressing/anonymous"如果端點使用 WSDL 1.1 SOAP 1.x HTTP 繫結，並有替代的原則`wsap:UsingAddressing`判斷提示，以及任何`cdp:CompositeDuplex`附加的判斷提示。  
  
 WS-Addressing WSDL 規格會試圖描述類似的通訊協定繫結，藉由引入具有三種文字值 (必要項、選擇性和禁止) 的 `<wsaw:Anonymous/>` 項目，指出`wsa:ReplyTo` 標頭 (第 3.2 節) 上的需求。 不巧的是，此類項目定義並無法特別當做 WS-Policy 內容的判斷提示使用，因為它需要網域專屬的延伸，以支援其他使用此類項目做為判斷提示的交集。 此類項目定義也指出了 `ReplyTo` 標頭的值，而非網路上的端點行為，如此將使其成為 HTTP 傳輸專屬的定義。  
  
#### <a name="action-definition"></a>動作定義  
 WS-Addressing 2004/08 為 `wsa:Action` 項目定義了 `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` 屬性。 WS-Addressing 1.0 WSDL 繫結 (WS-ADDR10-WSDL) 定義了一個類似的屬性，即 `wsaw10:Action`。  
  
 兩者間的不同處就只是預設的動作模式語意，這些部分分別在 WS-ADDR 的第 3.3.2 節和 WS-ADDR10-WSDL 的第 4.4.4 節中描述。  
  
 是具有兩個端點共用相同的合理`portType`（或合約，在 WCF 術語） 但會使用不同的 Ws-addressing 版本。 但考慮到該動作是由 `portType` 所定義，不應在實作 `portType` 的端點上變更，如此將難以支援兩種預設的動作模式。  
  
 若要解決這個爭論，WCF 支援的單一版本`Action`屬性。  
  
 B3521: WCF 使用`wsaw10:Action`屬性`wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]`元素，若要判斷 WS-ADDR10-WSDL 中定義`Action`URI 對應的訊息，不論端點所使用的 Ws-addressing 版本。  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a>使用 WSDL 連接埠內部的端點參考  
 WS-ADDR10-WSDL 第 4.1 節將 `wsdl:port` 元素延伸為包含 `<wsa10:EndpointReference…/>` 子元素，以便使用 WS-Addressing 的詞彙描述端點。 WCF 擴充的 Ws-addressing 2004/08 時，此公用程式允許`<wsa:EndpointReference…/>`顯示為的子元素`wsdl:port`。  
  
-   R3531：如果端點含有以 `<wsaw10:UsingAddressing/>`原則判斷提示取代之附加原則，則對應的 `wsdl:port` 項目可以包含一個子項目 `<wsa10:EndpointReference …/>`。  
  
-   R3532： 如果`wsdl:port`包含子元素`<wsa10:EndpointReference …/>`、`wsa10:EndpointReference/wsa10:Address`子項目值必須符合的值`@address`屬性的同層級`wsdl:port` / `wsdl:location`項目。  
  
-   R3533：如果端點含有以 `<wsap:UsingAddressing/>` 原則判斷提示替代的附加原則，則對應的 `wsdl:port` 項目可以包含子項目 `<wsa:EndpointReference …/>`。  
  
-   R3534： 如果`wsdl:port`包含子元素`<wsa:EndpointReference …/>`、`wsa:EndpointReference/wsa:Address`子項目值必須符合的值`@address`屬性的同層級`wsdl:port` / `wsdl:location`項目。  
  
### <a name="composition-with-ws-security"></a>與 WS-Security 組合  
 根據 WS-ADDR 和 WS-ADDR10 的安全性考量章節，建議將所有定址訊息標頭與訊息本文一起簽署，以將其繫結在一起。  
  
 當使用 WS-Security 保護訊息完整性時，WS-Addressing 訊息標頭以及從參考參數或屬性 (或兩者) 產生的標頭必須與訊息本文一起簽署。  
  
### <a name="examples"></a>範例  
  
#### <a name="one-way-message"></a>單向訊息  
 在這種情況下，傳送者會傳送單向訊息給接收者。 此時會使用 SOAP 1.2、HTTP 1.1 和 W3C WS-Addressing 1.0。  
  
 要求訊息結構：訊息標頭包含 `wsa10:To` 和 `wsa10:Action` 項目。 訊息本文包含來自應用程式命名空間的特定 `<app:Ping>` 項目。  
  
 HTTP 標頭： POST 的目的地符合中的 URI`wsa10:To`項目。  
  
 Content-Type 標頭具有 SOAP 1.2 所要求的 `application/soap+xml` 值。 其中包含參數 `charset` 和 `action`。 Content-Type 標頭的 `action` 參數符合 `wsa10:Action` 訊息標頭的值。  
  
```  
POST http://fabrikam123.com/Service HTTP/1.1  
Content-Type: application/soap+xml; charset=utf-8;    
              action="http://fabrikam123.com/Service/OneWay"  
Host: 131.107.72.15  
Content-Length: 1501  
Expect: 100-continue  
Proxy-Connection: Keep-Alive  
<s12:Envelope>  
  <s12:Header>  
    <wsa10:To s12:mustUnderstand="1">  
        http://fabrikam123.com/Service  
    </wsa10:To>  
    <wsa10:Action s12:mustUnderstand="1">  
        http://fabrikam123.com/Service/OneWay   
    </wsa10:Action>  
  </s12:Header>  
  <s12:Body>  
    <Ping xmlns="http://fabrikam123.com/Service/">  
      <Text>Hello World</Text>  
    </Ping>  
  </s12:Body>  
</s12:Envelope>  
```  
  
 接收者會以空的 HTTP 回應和狀態 202 回應。 以下為 HTTP 回應的範例：  
  
```  
HTTP/1.1 202 Accepted  
Date: Fri, 15 Jul 2005 08:56:07 GMT  
Server: Microsoft-IIS/6.0  
MicrosoftOfficeWebServer: 5.0_Pub  
X-Powered-By: ASP.NET  
X-AspNet-Version: 2.0.50215  
Cache-Control: private  
Content-Length: 0  
```  
  
## <a name="soap-message-transmission-optimization-mechanism"></a>SOAP 訊息傳輸最佳化機制  
 本章節將描述 HTTP SOAP MTOM 的 WCF 實作詳細資料。 MTOM 技術是類別的傳統的 text/XML 編碼或 WCF 二進位編碼相同的 SOAP 訊息編碼機制。 MTOM 包含下列各項：  
  
-   由 [XOP] 描述的 XML 編碼和封裝機制，會將 XML 資訊項目最佳化，將包含了以 Base64 編碼的二進位資料分割為不同的二進位部分。  
  
-   XOP 封裝 (Package) 的 MIME 封裝 (Encapsulation)，會將 XML Infoset 和每個 XOP 封裝的二進位部分序列化為不同的 MIME 部分。  
  
-   套用至 SOAP 1.x 封套的 MIME XOP 編碼。  
  
-   HTTP 傳輸繫結。  
  
 您可搭配使用 WCF 非 HTTP 傳輸的 MTOM。 不過，在本主題中，我們將專注在 HTTP 上。  
  
 MTOM 格式利用了大量的規格集，其中涵蓋了 MTOM 本身、XOP 和 MIME。 此規格集的模組化使其稍微難以重新建構格式及處理語意的正確需求。 本節將描述 MTOM HTTP 繫結的格式和處理需求。  
  
### <a name="mtom-message-encoding"></a>MTOM 訊息編碼  
  
#### <a name="generating-mtom-messages"></a>產生 MTOM 訊息  
 [XOP] 第 3.1 節描述具有項目資訊項目之 XML 編碼的程序，這些資訊項目會在抽象定義的 XOP 封裝中包含 Base64 值。  
  
 下列步驟的順序即描述了 MTOM 專屬的編碼程序：  
  
1.  確定 SOAP 封套已編碼包含沒有項目資訊項目`[namespace name]`的"http://www.w3.org/2004/08/xop/include"和`[local name]`的`Include`。  
  
2.  建立空白的 MIME 封裝。  
  
3.  識別原始 XML Infoset 內要進行最佳化的項目資訊項目。 對於要進行最佳化的項目，項目資訊項目標記為 `[children]` 的字元必須採用 `xs:base64Binary` 的標準格式 (請參閱 XSD-2、3.2.16 base64Binary)，並且在非空白字元內容之前、中間或之後，都不能有任何空白字元。  
  
4.  建立 XOP SOAP 封套 (為原始 SOAP 封套的複本)，但具有在先前步驟中以 `xop:Include` 項目資訊項目建構取代而識別的每個項目資訊項目，如下所示：  
  
    1.  藉由將其視為 Base64 編碼的資料進行處理，將取代的字元轉換為二進位資料。  
  
    2.  產生唯一的 Content-ID 標頭值，滿足 R3133 和 R3134 的需求。  
  
    3.  產生具有二進位值的 Content-Transfer-Encoding MIME 標頭。  
  
    4.  如果已最佳化的項目資訊項目 (最近插入 `xop:Include` 項目資訊項目的 [parent]) 具有 `xmime:contentType` 屬性資訊項目，則產生一個具有 `xmime:contentType` 屬性值的 Content-Type MIME 標頭。  
  
    5.  產生新的二進位 MIME 部分，具有採用二進位資料形式之內容，這些資料是從處理為 Base64 的取代字元解碼而來、來自 4b 的 Content-ID 標頭、來自 4c 的 Content- Transfer-Encoding 標頭、若在步驟 4d 產生則為 Content-Type 標頭。  
  
    6.  將 `href` 屬性加入至 `xop:Include` 項目，該項目具有 cid: uri 值，衍生自步驟 4b 中產生的 Content-ID 標頭值。 移除封閉"\<"和">"字元、 URL 逸出的剩餘字串，並加入前置詞`cid:`。 下列最小字元集為 RFC1738 和 RFC2396 逸出所需。 其他可以逸出的字元。  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  建立根 MIME 部分，具有來自步驟 4 的 XOP SOAP 封套。  
  
6.  撰寫 HTTP 標頭，包括 HTTP Content-Type 標頭。  
  
7.  撰寫 MIME 封裝。  
  
#### <a name="processing-mtom-messages"></a>處理 MTOM 訊息  
 MTOM 訊息的處理正是如先前「產生 MTOM 訊息」一節所述的反向程序：  
  
1.  確定根 MIME 部分具有 Content-Type `application/xop+xml`。  
  
2.  藉由剖析封裝為 XML 文件的根 MIME 部分，以建構 SOAP 封套。 字元編碼是由根 MIME 部分的 Content-Type `charset` 參數所決定的。  
  
3.  對於已建構 SOAP 封套內的每個項目資訊項目，其中具有一個 `xop:Include` 項目資訊項目，做為其 [children] 屬性的唯一成員：  
  
    1.  移除 `cid:` 前置詞，並以 `@href` 項目的 `xop:Include` 屬性值解除所有 URI 逸出順序的逸出 (RFC 2396)。 括住結果字串中的"\<"，">"。  
  
    2.  找出具有 Content-ID 標頭值的 MIME 部分，其符合衍生自步驟 3a 的字串。  
  
    3.  取代 `xop:Include` 項目資訊項目，它出現在每個項目的 `children` 屬性中，具有代表標準 Base64 編碼的字元資訊項目 (請參閱 XSD-2、3.2.16 base64Binary)，這些項目是步驟 3b 內識別的 MIME 部分之實體主體 (實際上以從封裝部分重新建構的資料取代 `xop:Include` 項目資訊項目)。  
  
#### <a name="http-content-type-header"></a>HTTP Content-Type 標頭  
 下列是 WCF 說明 SOAP 1.x MTOM 編碼訊息的衍生自 MTOM 規格本身內的 HTTP Content-type 標頭格式的清單，以及衍生自 MTOM 和 RFC 2387。  
  
-   R4131：HTTP Content-Type 標頭必須具有多重/相關 (區分大小寫) 的值，以及其參數。 參數名稱是區分大小寫的。 參數的順序並不重要。  
  
-   MIME 訊息之 Content-Type 標頭的完整巴克斯格式 (Backus-Naur Form，BNF) 列示於 RFC 2045 第 5.1 節中。  
  
-   R4132：HTTP Content-Type 標頭必須具有含 `application/xop+xml` 值的型別參數，以雙引號括住。  
  
 雖然使用雙引號不是在 RFC 2387 中明確陳述，文字會遵守多重/相關媒體型別參數的最可能包含的所有保留的字元，例如"@" or "/"，因此需要使用雙引號。  
  
-   R4133：HTTP Content-Type 標頭應該具有起始參數，其中具有包含 SOAP 1.x 封套之 MIME 部分的 Content-ID 標頭值，以雙引號括住。 如果省略了起始參數，則第一個 MIME 部分必須包含 SOAP 1.x 封套。  
  
-   R4134：以 SOAP 1.1 MTOM 編碼之訊息的 HTTP Content-Type 標頭必須包含 start-info 參數，其具有 text/xml 的值，以雙引號括住。  
  
-   R4135：以 SOAP 1.2 MTOM 編碼之訊息的 HTTP Content-Type 標頭必須包含 start-info 參數，其具有 `application/soap+xml` 值，以雙引號括住。  
  
-   R4136：以 SOAP 1.x MTOM 編碼之訊息的 HTTP Content-Type 標頭必須具有界限參數，其值 (以雙引號括住) 符合 RFC 2046 第 5.1.1 節內所定義的 MIME 界限 BNF 值。  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     例如：  
  
     正確  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     正確  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     不正確  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a>Infoset MIME 部分  
 SOAP 1.x 封套會封裝為 XOP MIME 封裝的根部分，通常稱為 `infoset` 部分。  
  
-   R4141：SOAP 1.x 封套必須封裝為 XOP MIME 封裝的根部分，稱為 `infoset` 部分，並從 HTTP Content-Type 參考。  
  
-   R4142：SOAP `Infoset` 部分必須包含下列 MIME 標頭：`Content-ID`、`Content-Transfer-Encoding` 和 `Content-Type`。  
  
 Content-ID 標頭的格式在 RFC 2045 中定義為  
  
```  
"Content-ID" ":" msg-id  
```  
  
 其中 `msg-id` 在 RFC 2822 (取代 RFC 822，在 RFC 2045 內參考) 中定義為：  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 和都有效的電子郵件地址住"\<"和">"。 RFC 2822 內加入了 `[CFWS]` 前置和後置字元，用以帶出註解，且不應用於保留互通性。  
  
 R4143：Infoset MIME 部分的 Content-ID 標頭值必須遵守 RFC 2822 實際執行的 `msg-id`，其中省略了 `[CFWS]` 前置和後置字元部分。  
  
 許多 MIME 實作嚴謹需求住值"\<"和">"是電子郵件地址並用`absoluteURI`括住"\<"，">"除了電子郵件地址。 這個版本的 WCF 使用表單的 CONTENT-ID MIME 標頭的值：  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 R4144：MTOM 處理器應該接受符合下列較不嚴謹之 `msg-id` 的 Content-ID 標頭值。  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 MIME (RFC 2045) 提供 Content-Transfer-Encoding 標頭，用於溝通 MIME 部分的內容編碼。 Content-Transfer-Encoding 預設定義為 7 位元，不適用於大部分的 SOAP 訊息，因此需要使用 Content-Transfer-Encoding 標頭提供較佳的互通性：  
  
-   R4145：SOAP Infoset 部分必須包含 Content-Transfer-Encoding 標頭。  
  
-   R4146：如果 SOAP 封套字元的編碼為 UTF-8，Content-Transfer-Encoding 標頭的值必須為 8 位元。  
  
-   R4147：如果 SOAP 封套的字元編碼為 UTF-16，則 Content-Transfer-Encoding 標頭的值必須為二進位值。  
  
-   根據 [XOP] 第 5 節，  
  
-   R4148: SOAP1.1 Infoset 部分必須包含 Content-type 標頭與媒體類型的應用程式/xop + xml，且參數類型 ="text/xml"和字元集  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   R4149: SOAP 1.2 Infoset 部分必須包含 Content-type 標頭與媒體類型`application/xop+xml`且參數類型 ="`application/soap+xml`"和`charset`。  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     雖然 XOP 將 `charset` 的 `application/xop+xml` 參數定義為選擇性參數，您仍舊需要使用此參數為 `charset` 媒體類型的 `text/xml` 參數提供類似於 BP 1.1 需求的互通性。  
  
-   R41410：`type` 和 `charset` 參數必須存在於 SOAP 1.x Infoset 部分的 Content-Type 標頭上。  
  
#### <a name="wcf-endpoint-support-for-mtom"></a>MTOM 的 WCF 端點支援  
 MTOM 的目的是要對 SOAP 訊息進行編碼，以最佳化 Base64 編碼的資料。 以下為條件約束的清單：  
  
-   R4151：任何包含 Base64 編碼資料的項目資訊項目可能都已進行了最佳化。  
  
-   B4152: WCF 最佳化項目資訊項目包含 base64 編碼資料，且超過 1024 個位元組的長度。  
  
 設定為使用 MTOM 的 WCF 端點仍會一律傳送 MTOM 編碼訊息。 即使沒有任何部分滿足所要求的準則，訊息仍舊會以 MTOM 編碼 (序列化為 MIME 封裝，其中具有含 SOAP 封套的單一 MIME 部分)。  
  
### <a name="ws-policy-assertion-for-mtom"></a>MTOM 的 WS-Policy 判斷提示  
 WCF 會使用下列原則判斷提示，指出 MTOM 使用量端點：  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   R4211：之前的原則判斷提示具有端點原則主體，並指定所有傳送訊息和接收訊息的端點必須使用 MTOM 進行最佳化。  
  
-   B4212： 當設定為使用 MTOM 最佳化時，WCF 端點將 MTOM 原則判斷提示附加至對應的原則`wsdl:binding`。  
  
### <a name="composition-with-ws-security"></a>與 WS-Security 組合  
 MTOM 是一種編碼機制，類似於`text/xml`和 WCF 二進位 XML。 MTOM 可與 WS-Security 和其他 WS-* 通訊協定自然組合：使用 MTOM，可以使 WS-Security 保護的訊息最佳化。  
  
### <a name="examples"></a>範例  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>使用 MTOM 進行編碼的 WCF SOAP 1.1 訊息  
  
```  
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1  
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"  
Content-Type: multipart/related;type="application/xop+xml";  
              start="<http://tempuri.org/0>";start-info="text/xml";  
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
Host: 131.107.72.15  
Content-Length: 1501  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
Content-ID: <http://tempuri.org/0>  
Content-Transfer-Encoding: 8bit  
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Body>  
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">  
      <array>  
        <xop:Include   
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"   
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
      </array>  
    </EchoBinaryAsString>  
  </s:Body>  
</s:Envelope>  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
Content-ID: <http://tempuri.org/1/632618206521093670>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
…Binary Content..  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
```  
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>使用 MTOM 對 WCF Secure SOAP 1.2 訊息進行編碼  
 在此範例中，訊息是以 MTOM 和 SOAP 1.2 進行編碼，並使用 WS-Security 予以保護。 用於識別編碼的二進位部分是 `BinarySecurityToken`的內容，以及對應於已加密簽章和已加密主體之 `CipherValue` 的 `EncryptedData`。 請注意，`CipherValue`的`EncryptedKey`未識別最佳化由 WCF，因為其長度小於 1024 位元組。  
  
```  
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1  
Content-Type: multipart/related; type="application/xop+xml";  
              start="<http://tempuri.org/0>";  
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";  
              start-info="application/soap+xml";   
              action="http://xmlsoap.org/echoBinaryAsString"  
Host: 131.107.72.15  
Content-Length: 1941  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/0>  
Content-Transfer-Encoding: 8bit  
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
  <s:Header>  
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">  
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>  
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>  
      </u:Timestamp>  
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">  
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
      </o:BinarySecurityToken>  
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>  
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
          <o:SecurityTokenReference>  
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>  
          </o:SecurityTokenReference>  
        </KeyInfo>  
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>  
        </e:CipherData>  
      </e:EncryptedKey>  
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">  
        <o:SecurityTokenReference>  
          <o:Reference URI="#_1"/>  
        </o:SecurityTokenReference>  
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>  
      </c:DerivedKeyToken>  
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:DataReference URI="#_3"/>  
        <e:DataReference URI="#_4"/>  
      </e:ReferenceList>  
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>  
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
          <o:SecurityTokenReference>  
            <o:Reference URI="#_2"/>  
          </o:SecurityTokenReference>  
        </KeyInfo>  
        <e:CipherData>  
          <e:CipherValue>  
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
          </e:CipherValue>  
        </e:CipherData>  
      </e:EncryptedData>  
    </o:Security>  
  </s:Header>  
  <s:Body u:Id="_0">  
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>  
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
          <o:Reference URI="#_2"/>  
        </o:SecurityTokenReference>  
      </KeyInfo>  
      <e:CipherData>  
        <e:CipherValue>  
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
        </e:CipherValue>  
      </e:CipherData>  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/1/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary content of BinarySecurityToken - X509 Certificate...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/2/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary serialization of the encrypted primary signature...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/3/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary serialization of the encrypted Body...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--  
```
