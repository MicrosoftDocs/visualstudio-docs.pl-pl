---
title: 'DA0014: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk | Dokumentacja firmy Microsoft'
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
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba6695b4705a29264f29fa79d23a63062151a62e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730589"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014: Wyjątkowo wysoki stopień stronicowania aktywnej pamięci na dysku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0014 |  
| Kategoria | Pamięci i stronicowania |  
| Metoda profilowania | Wszystkie |  
| Komunikat | Odbywa się bardzo wysoki stopień stronicowania aktywnej pamięci na dysk. Aplikacja może być powiązane z pamięci. |  
| Typ reguły | Ostrzeżenie |  
  
 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 25 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Dane o wydajności systemu, które zostały zebrane podczas uruchomienia profilowania wskazuje bardzo wysoki stopień stronicowania aktywnej pamięci na i z dysku, które wystąpiły w całym uruchomienia profilowania. Stronicowanie stawki na tym poziomie zwykle wpływa na wydajność aplikacji i czasu odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez modyfikowanie algorytmów. Może być również konieczne należy wziąć pod uwagę wymagania dotyczące pamięci aplikacji. uruchomione ponownie profilowanie na komputerze więcej pamięci.  
  
## <a name="rule-description"></a>Opis reguły  
 Nadmierne stronicowania na dysku może być spowodowany brakiem pamięci fizycznej. Jeśli operacja stronicowania dominują użycie dysku fizycznego, w którym znajduje się plik stronicowania, mogą one spowolnić inne operacje dysk korzystający z aplikacji na tym samym dysku.  
  
 Często strony są dysku zapisu lub odczytu z dysku podczas operacji stronicowania zbiorczego. Na przykład jest często znacznie większa niż liczba zapisy stron/s, liczba stron wyjścia na sekundę. Ponieważ dane wyjściowe strony na sekundę obejmuje również stron zmienione dane z pamięci podręcznej systemu plików. Jednak nie zawsze jest proste ustalenie, który proces jest bezpośrednio odpowiedzialna za stronicowanie i dlaczego.  
  
> [!NOTE]
>  Ta reguła jest uruchamiana, gdy stopień stronicowania aktywnej pamięci osiągną bardzo wysoki współczynnik. Reguły informacyjne, jeśli poziom stronicowania jest istotne, ale nie extreme [DA0017: intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md) generowane w zamian.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [znaczniki](../profiling/marks-view.md) widoku. Znajdź **Pamięć\Strony/s** kolumny. Określa, czy określone faz wykonywania programu stronicowania działanie we/wy w przypadku większych niż inne.  
  
 Jeśli jest zbieranie danych profilu dla aplikacji ASP.NET w scenariuszu testów obciążenia, spróbuj uruchomić ponownie test obciążenia na komputerze, który został skonfigurowany za pomocą dodatkowej pamięci fizycznej (i pamięci RAM).  
  
 Rozważ zmniejszenie alokacji pamięci, zmiana algorytmów i unikanie interfejsów API wymagających dużej ilości pamięci, takich jak String.concat — i String.Substring.



