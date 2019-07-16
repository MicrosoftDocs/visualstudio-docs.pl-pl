---
title: '&lt;Podpis&gt; — Element (wdrażanie ClickOnce) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df18b63ff306525cba74ef0932c97edd64eee797
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198116"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Podpis&gt; — Element (wdrażanie ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera informacje potrzebne do cyfrowego podpisywania to manifest wdrożenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Uwagi  
 Podpisywania manifestu wdrożenia za pomocą podpisu koperty jest opcjonalne, ale zalecane. Aby uzyskać więcej informacji na temat podpisywania XML plików Zobacz World Wide Web Consortium zalecenia, "Podpis XML składni i przetwarzanie" opisane w [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).  
  
 Jeśli chcesz zarejestrować manifeście skróty należy określić dla wszystkich plików. Nie można podpisać manifest z plikami, które nie mają formę skrótu, ponieważ użytkownicy nie może sprawdzić zawartości bez haszowania plików.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano `Signature` elementu w manifeście wdrożenia, używane w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia.  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)
