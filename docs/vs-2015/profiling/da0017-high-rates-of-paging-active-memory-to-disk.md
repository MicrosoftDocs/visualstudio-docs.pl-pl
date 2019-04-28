---
title: 'DA0017: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 00df8bf8757b9dba35537942716c37f66675bf32
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435866"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Intensywne stronicowanie aktywnej pamięci na dysk
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rule Id|DA0017|  
| Kategoria | Pamięci i stronicowania |  
| Metoda profilowania | Wszystkie |  
| Komunikat | Występuje wysoki stopień stronicowania aktywnej pamięci na dysk. Aplikacja może być powiązane z pamięci. |  
| Typ reguły | Informacji |  
  
 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Dane o wydajności systemu, które zostały zebrane podczas uruchomienia profilowania wskazuje wysoki stopień stronicowania aktywnej pamięci na i z dysku, które wystąpiły w całym uruchomienia profilowania. Stawki stronicowania na tym poziomie zwykle będzie miało wpływ na wydajność aplikacji i czasu odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez modyfikowanie algorytmów. Może być również konieczne należy wziąć pod uwagę wymagania dotyczące pamięci aplikacji.  
  
## <a name="rule-description"></a>Opis reguły  
  
> [!NOTE]
> Ta reguła informacyjny jest uruchamiana, gdy stopień stronicowania aktywnej pamięci osiągną znaczną ilość. Gdy wystąpi bardzo wysoki stopień stronicowania, zasada ostrzeżenia [DA0014: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md) generowane w zamian.  
  
 Nadmierne stronicowania na dysku może być spowodowany brakiem pamięci fizycznej. Jeśli operacja stronicowania dominują użycie dysku fizycznego, w którym znajduje się plik stronicowania, mogą one spowolnić inne operacje dysk korzystający z aplikacji na tym samym dysku.  
  
 Strony są często dysku zapisu lub odczytu z dysku podczas operacji stronicowania zbiorczego. Liczba stron wyjścia na sekundę odbywa się znacznie większy niż numer zapisy stron/s, na przykład. Ponieważ dane wyjściowe strony na sekundę obejmuje również stron zmienione dane z pamięci podręcznej systemu plików. Jednak nie zawsze jest proste ustalenie, który proces jest bezpośrednio odpowiedzialna za stronicowanie i dlaczego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [znaczniki](../profiling/marks-view.md) widoku. Znajdź **Pamięć\Strony/s** kolumny. Określa, czy określone faz wykonywania programu stronicowania działanie we/wy w przypadku większych niż inne.  
  
 Jeśli jest zbieranie danych profilu dla aplikacji ASP.NET w scenariuszu testów obciążenia, spróbuj uruchomić ponownie test obciążenia na komputerze, który został skonfigurowany za pomocą dodatkowej pamięci fizycznej (i pamięci RAM).  
  
 Rozważ zmniejszenie alokacji pamięci, zmiana algorytmów i unikanie interfejsów API wymagających dużej ilości pamięci, takich jak String.concat — i String.Substring.
