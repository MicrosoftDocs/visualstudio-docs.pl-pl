---
title: 'DA0001: Użyj StringBuilder do łączenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb8da704832031d69156eee8863b689e7956f025
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295954"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Używaj StringBuilder do łączenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [DA0001: use StringBuilder for rezłączs](https://docs.microsoft.com/visualstudio/profiling/da0001-use-stringbuilder-for-concatenations).  
  
|||  
|-|-|  
|Identyfikator zasady|DA0001|  
|Kategoria|Użycie .NET Framework|  
|Metody profilowania|Sond<br /><br /> Oprzyrządowanie|  
|Komunikat|Rozważ użycie StringBuilder dla łączenia ciągów|  
|Typ komunikatu|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 Wywołania metody System. String. Concat są znaczną częścią danych profilowania. Rozważ użycie klasy <xref:System.Text.StringBuilder> do konstruowania ciągów z wielu segmentów.  
  
## <a name="rule-description"></a>Opis reguły  
 Obiekt <xref:System.String> jest niezmienny. W związku z tym wszystkie modyfikacje ciągu tworzą nowy obiekt String i wyrzucanie elementów bezużytecznych. Takie zachowanie jest takie samo, niezależnie od tego, czy wywoływana jest metoda String. Concat jawnie, czy też użyto operatorów łączenia ciągów, takich jak + lub + =. Wydajność programu można zmniejszyć, jeśli te metody są często wywoływane, na przykład gdy znaki są dodawane do ciągu w ścisłej pętli.  
  
 Klasa StringBuilder jest obiektem modyfikowalnym i, w przeciwieństwie do System. String, większość metod w StringBuilder modyfikujących wystąpienie tej klasy zwraca odwołanie do tego samego wystąpienia. Można wstawiać znaki lub dołączać tekst do wystąpienia StringBuilder i usuwać lub zastępować znaki w wystąpieniu bez konieczności alokowania nowego wystąpienia i usuwania oryginalnego wystąpienia.  
  
## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku Szczegóły funkcji](../profiling/function-details-view.md) danych profilu próbkowania. Znajdź sekcje programu, które najczęściej używają łączenia ciągów. Użyj klasy StringBuilder do obsługi złożonych ciągów, w tym częstych operacji łączenia ciągów.  
  
 Aby uzyskać więcej informacji na temat sposobu pracy z ciągami, sekcja [operacje na ciągach](https://go.microsoft.com/fwlink/?LinkId=177816) w [rozdziale 5 — Ulepszanie wydajności kodu zarządzanego](https://go.microsoft.com/fwlink/?LinkId=177817) w bibliotece Microsoft Patterns and Practices.
