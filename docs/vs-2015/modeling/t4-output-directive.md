---
title: T4 Output — dyrektywa | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9262ec994ec847c38ec8d5c1ad95010a929cc4ba
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834523"
---
# <a name="t4-output-directive"></a>Dyrektywa T4 Output
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonów tekstowych `output` dyrektywa jest używany do definiowania rozszerzenia nazwy pliku i kodowanie pliku przekształcone.  
  
 Na przykład jeśli Twoja [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekt zawiera plik szablonu o nazwie **MyTemplate.tt** zawierającą następujące dyrektywy:  
  
 `<#@output extension=".cs"#>`  
  
 następnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wygeneruje plik o nazwie **MyTemplate.cs**  
  
 `output` Dyrektywy nie jest wymagany w szablon tekstowy (wstępnie przetworzony) czasu wykonywania. Zamiast tego aplikacja uzyskuje wygenerowany ciąg przez wywołanie metody `TextTransform()`. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="using-the-output-directive"></a>Za pomocą dane wyjściowe — dyrektywa  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 Powinna istnieć nie więcej niż jednego `output` dyrektywy w każdym szablonie tekstu.  
  
## <a name="extension-attribute"></a>Atrybut rozszerzenia  
 Określa rozszerzenie nazwy pliku wyjściowego pliku wygenerowanego tekstu.  
  
 Wartość domyślna to **.cs**  
  
 Przykłady:  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Dopuszczalne wartości:  
 Wszelkie nieprawidłowe rozszerzenie nazwy pliku.  
  
## <a name="encoding-attribute"></a>Atrybut kodowania  
 Określa kodowanie do użycia podczas generowania pliku wyjściowego. Na przykład:  
  
 `<#@ output encoding="utf-8"#>`  
  
 Wartość domyślna to kodowanie używane przez plik szablonu tekstu.  
  
 Dopuszczalne wartości:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` (Ustawienie domyślne systemu)  
  
 Ogólnie rzecz biorąc, można użyć ciągu nazwasieciweb lub numer strony kodowej dowolnego kodowania zwrócony przez <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
