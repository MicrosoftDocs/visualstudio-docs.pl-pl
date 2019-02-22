---
title: 'DA0017: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc304a90f9d51611ad2455c130e589aa0204cdc5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56620489"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk

|||
|-|-|
|Identyfikator reguły|DA0017|
|Kategoria|Pamięci i stronicowania|
|Metoda profilowania|Wszystkie|
|Komunikat|Występuje wysoki stopień stronicowania aktywnej pamięci na dysk. Aplikacja może być powiązane z pamięci.|
|Typ reguły|Informacje|

 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.

## <a name="cause"></a>Przyczyna
 Dane o wydajności systemu, które zostały zebrane podczas uruchomienia profilowania wskazuje wysoki stopień stronicowania aktywnej pamięci na i z dysku, które wystąpiły w całym uruchomienia profilowania. Stawki stronicowania na tym poziomie zwykle będzie miało wpływ na wydajność aplikacji i czasu odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez modyfikowanie algorytmów. Może być również konieczne należy wziąć pod uwagę wymagania dotyczące pamięci aplikacji.

## <a name="rule-description"></a>Opis reguły

> [!NOTE]
>  Ta reguła informacyjny jest uruchamiana, gdy stopień stronicowania aktywnej pamięci osiągną znaczną ilość. Gdy wystąpi bardzo wysoki stopień stronicowania, zasada ostrzeżenia [DA0014: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md) generowane w zamian.

 Nadmierne stronicowania na dysku może być spowodowany brakiem pamięci fizycznej. Jeśli operacja stronicowania dominują użycie dysku fizycznego, w którym znajduje się plik stronicowania, mogą one spowolnić inne operacje dysk korzystający z aplikacji na tym samym dysku.

 Strony są często dysku zapisu lub odczytu z dysku podczas operacji stronicowania zbiorczego. Liczba stron wyjścia na sekundę odbywa się znacznie większy niż numer zapisy stron/s, na przykład. Ponieważ dane wyjściowe strony na sekundę obejmuje również stron zmienione dane z pamięci podręcznej systemu plików. Jednak nie zawsze jest proste ustalenie, który proces jest bezpośrednio odpowiedzialna za stronicowanie i dlaczego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [znaczniki](../profiling/marks-view.md) widoku. Znajdź **Pamięć\Strony/s** kolumny. Określa, czy określone faz wykonywania programu stronicowania działanie we/wy w przypadku większych niż inne.

 Jeśli jest zbieranie danych profilu dla aplikacji ASP.NET w scenariuszu testów obciążenia, spróbuj uruchomić ponownie test obciążenia na komputerze, który został skonfigurowany za pomocą dodatkowej pamięci fizycznej (i pamięci RAM).

 Rozważ zmniejszenie alokacji pamięci, zmiana algorytmów i unikanie interfejsów API wymagających dużej ilości pamięci, takich jak String.concat — i String.Substring.