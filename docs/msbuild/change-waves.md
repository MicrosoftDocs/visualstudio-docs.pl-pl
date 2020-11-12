---
title: Zmień fale
description: Dowiedz się, jak włączyć lub wyłączyć funkcje w programie MSBuild, które potencjalnie zakłócają działanie.
ms.date: 11/10/2020
ms.topic: conceptual
helpviewer_keywords:
- Change waves [MSBuild]
- MSBuildDisableFeaturesFromVersion environment variable
author: ghogen
ms.author: ghogen
manager: jillfra
monikerRange: '>=vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 68aafd8ebb97b4bf649cc41eb7739e1700c9cb1a
ms.sourcegitcommit: 83a39d48b00c6c351e5c1707942633b7f73aaad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2020
ms.locfileid: "94532073"
---
# <a name="change-waves"></a>Zmień fale

*Fala zmiany* to zestaw zmian zachowania w programie MSBuild, z których można zrezygnować, określając konkretną flagę jako zmienną środowiskową. Celem tej funkcji jest ostrzeganie o potencjalnie niezakłóconych zmianach, dzięki czemu można elastycznie dostosować się do tych zmian, zanim staną się one standardowe. Wszystkie funkcje w określonej fazie zmiany mogą być włączone lub wyłączone jednocześnie, a nie osobno.

Po uaktualnieniu do nowej wersji programu MSBuild, wprowadzane zmiany są domyślnie włączone, ale jeśli funkcja ma negatywny wpływ na kompilację, można łatwo wyłączyć tę zmianę. Każda fala zmian jest identyfikowana przez numer wersji programu MSBuild (na przykład 16,8), ale ustawienie Wave Change kontroluje tylko niektóre funkcje, które mają wpływ na proces kompilacji, a nie wszystkie zmiany w wersji programu MSBuild. Lista funkcji w każdej fazie zmiany zostanie wyświetlona [w dalszej części tego artykułu](#change-waves-and-associated-features). Wyłączenie zmiany Wave powoduje także wyłączenie zmian w przypadku wyższych wersji.

## <a name="opt-out-of-change-wave-features"></a>Rezygnacja z zmiany funkcji Wave

Aby wyłączyć funkcje w fazie zmiany, Ustaw zmienną środowiskową `MSBuildDisableFeaturesFromVersion` na wartość Wave (lub wersję programu MSBuild), która zawiera funkcję, która ma zostać **wyłączona**. Jest to wersja programu MSBuild, dla którego zostały opracowane funkcje. Zobacz mapowanie zmian do poniższych funkcji.

### <a name="msbuilddisablefeaturesfromversion-values"></a>MSBuildDisableFeaturesFromVersion wartości

Jeśli nie ustawisz prawidłowego rzutu zmiany, otrzymasz ostrzeżenie i/lub wartość domyślną dla konkretnej fazy `MSBuildDisableFeaturesFromVersion` . W poniższej tabeli przedstawiono możliwe ustawienia:

| `MSBuildDisableFeaturesFromVersion` Wartościami                         | Wynik        | Czy odebrać ostrzeżenie? |
| :-------------                                                    | :----------   | :----------: |
| Usunięt                                                             | Włącz wszystkie fale zmian, co oznacza, że wszystkie funkcje związane z każdą zmianą zmiany są włączone.               | Nie   |
| Wszystkie prawidłowe i bieżące Wave zmiany (na przykład `16.8` )                      | Wyłącz wszystkie funkcje w tle Wave `16.8` **i wyższych**.                                           | Nie   |
| Nieprawidłowa wartość (na przykład `16.9` gdy prawidłowe fale to `16.8` i `16.10` )| Domyślnie do najbliższej prawidłowej wartości (rosnąco). Na przykład ustawienie `16.9` będzie domyślnie `16.10` .               | Nie   |
| Poza rotacją (na przykład `17.1` gdy najwyższa fala jest `17.0` )      | Ogranicz do najbliższej prawidłowej wartości. Na przykład, zostaje zamocowany `17.1` do i zostaje zamocowany do `17.0` `16.5``16.8`                    | Tak  |
| Nieprawidłowy format (na przykład, `16x8` , `17_0` `garbage` )                    | Włącz wszystkie fale zmian, co oznacza, że wszystkie funkcje związane z każdą zmianą zmiany są włączone.               | Tak  |

## <a name="change-waves-and-associated-features"></a>Zmień fale i powiązane funkcje

Linki na poniższej liście przechodzą do usługi GitHub PR dla tej funkcji.

### <a name="168"></a>16,8

- [Włącz nowarn](https://github.com/dotnet/msbuild/pull/5671)
- [Obcinanie komunikatów dziennika pominięte miejsce docelowe/zadanie do 1024 znaków](https://github.com/dotnet/msbuild/pull/5553)
- [Nie Rozwijaj pełnego dysku elementy globalne z warunkiem false](https://github.com/dotnet/msbuild/pull/5669)

### <a name="1610"></a>16,10

- [Błąd, gdy właściwość rozszerzająca w warunku ma odstęp](https://github.com/dotnet/msbuild/pull/5672)

### <a name="170"></a>17,0

Nie ma jeszcze żadnych wpisów w tej fazie zmiany.

## <a name="change-waves-that-are-out-of-rotation"></a>Zmień fale, które nie są obracane

W tej chwili nie ma żadnych zmian w trakcie zmiany obrotu.

## <a name="faq"></a>Często zadawane pytania

**Dlaczego należy kierować każdą inną wersję, aby obrócić zmianę?**

Uważamy, że jest to wystarczająco dużo czasu, aby dyskusje z tymi, których to dotyczy, i pomóc w dostosowaniu do zmian.

**Dlaczego zmienna środowiskowa i nie jest właściwością projektu?**

Istnieją scenariusze, w których chcemy umieścić funkcję w fazie zmiany, przed załadowaniem projektu przez program MSBuild. Z tego powodu zmiany fal wymagają użycia zmiennych środowiskowych.

**Dlaczego warto wybrać opcję rezygnacji?**

Rezygnacja z tej firmy jest lepszym rozwiązaniem. w przeciwnym razie prawdopodobnie otrzymasz ograniczoną opinię, gdy funkcja ma wpływ na kompilacje klientów.

## <a name="see-also"></a>Zobacz także

- [MSBuild](msbuild.md)
- [Co nowego w programie MSBuild 16](whats-new-msbuild-16-0.md)
