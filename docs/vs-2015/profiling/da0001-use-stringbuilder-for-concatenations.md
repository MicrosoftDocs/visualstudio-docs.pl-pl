---
title: 'DA0001: Używaj StringBuilder do konkatenacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cbfbabc96273f6a39a69888025b80d12103dd4b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803321"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Używaj StringBuilder do łączenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio 2017, zobacz [DA0001: Używaj StringBuilder do konkatenacji](https://docs.microsoft.com/visualstudio/profiling/da0001-use-stringbuilder-for-concatenations) w witrynie docs.microsoft.com.  
  
|||  
|-|-|  
|Identyfikator reguły|DA0001|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metod profilowania|Próbkowania<br /><br /> Oprzyrządowanie|  
|Komunikat|Należy wziąć pod uwagę przy użyciu klasy StringBuilder do konkatenacji ciągów|  
|Typ komunikatu|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 Wywołania System.String.Concat są znaczna część danych profilowania. Należy rozważyć użycie <xref:System.Text.StringBuilder> klasy w celu tworzenia ciągów z wielu segmentów.  
  
## <a name="rule-description"></a>Opis reguły  
 Element <xref:System.String> obiektu jest niezmienny. W związku z tym żadnych modyfikacji ciągu tworzy nowy obiekt ciągu i wyrzucanie elementów bezużytecznych oryginału. To zachowanie jest taki sam, czy należy jawnie wywołać String.concat — lub operatory łączenia ciągów takich jak + lub +=... Można zmniejszyć wydajność programu, jeśli te metody są często wywoływane, takie jak kiedy znaki są dodawane do ciągu w pętli.  
  
 Klasy StringBuilder jest modyfikowalny obiekt i, w odróżnieniu od System.String, większość metod StringBuilder, które modyfikują wystąpienia tej klasy zwrócić odwołanie do tego samego wystąpienia. Można Wstawianie znaków lub dołączyć tekst do wystąpienia klasy StringBuilder i usunąć lub zastąpić znaki w wystąpieniu bez konieczności alokowania nowe wystąpienie i usunięcie oryginalnego wystąpienia.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widok szczegółów funkcji](../profiling/function-details-view.md) pobierania próbek danych jej profilu. Znajdź części programu, które najczęściej wykorzystać ciągów. Użyj klasy StringBuilder do złożonych działań na ciągach, w tym operacje na ciągach częste łączenia.  
  
 Aby uzyskać więcej informacji na temat sposobu pracy z ciągami [operacje na ciągach](http://go.microsoft.com/fwlink/?LinkId=177816) części [rozdział 5 - poprawę wydajności kodu zarządzanego](http://go.microsoft.com/fwlink/?LinkId=177817) w bibliotece Microsoft Patterns and Practices.

