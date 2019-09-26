---
title: Rozwiązywanie zestawów w czasie projektowania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 131cc61614c9f3e814cca5bcbc0ff6db303414cf
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253757"
---
# <a name="resolve-assemblies-at-design-time"></a>Rozwiązywanie zestawów w czasie projektowania
Po dodaniu odwołania do zestawu za pośrednictwem karty **.NET** okna dialogowego **Dodaj odwołanie** , odwołanie wskazuje do pośredniego zestawu odwołania; oznacza to, że zestaw, który zawiera wszystkie informacje o typie i podpisie, ale niekoniecznie zawiera kod. Karta **.NET** zawiera listę zestawów referencyjnych, które odpowiadają zestawom środowiska uruchomieniowego w .NET Framework. Ponadto zawiera listę zestawów referencyjnych, które odpowiadają zestawom środowiska uruchomieniowego w zarejestrowanych folderach AssemblyFoldersEx, które są używane przez inne firmy.

## <a name="multi-targeting"></a>Wiele elementów docelowych
 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] pozwala na wybór wersji .NET Framework, która działa albo w Środowisku uruchomieniowym języka wspólnego (CLR) wersja 2 lub wersja 4. Te wersje obejmują .NET Framework wersje 2,0, 3,0, 3,5, 4, 4,5 i 4.5.1 oraz wersje Silverlight, 1,0 i 2,0. Jeśli zostanie wydana nowa wersja .NET Framework oparta na wersji CLR 2.0 lub wersji 4, Framework może być zainstalowany przy użyciu odpowiedniego pakietu i automatycznie pojawi się jako cel w programie Visual Studio.

## <a name="how-type-resolution-works"></a>Jak działa rozpoznawanie typów
 W czasie wykonywania środowisko CLR rozpoznaje typy w zestawie, przeszukując pamięć podręczną, katalog *bin* i wszystkie ścieżki sondowania. Jest to obsługiwane przez moduł ładujący fusion. Ale skąd moduł ładujący fusion wie czego szukać? Jest to zależne od rozdzielczości w czasie projektowania, gdy aplikacja jest skompilowana.

 Podczas kompilacji, kompilator rozwiązuje typy aplikacji używając zestawów odwołania. W .NET Framework wersje 2,0, 3,0, 3,5, 4, 4,5 i 4.5.1 zestawy referencyjne są instalowane podczas instalacji .NET Framework.

 Zestawy odwołania są dostarczane przez pakiet docelowy, który jest dostarczany z odpowiednią wersją .NET Framework SDK. Framework sam w sobie dostarcza tylko zestawy środowiska uruchomieniowego. W celu skompilowania aplikacji należy zainstalować zarówno .NET Framework jak i odpowiadające mu .NET Framework SDK.

 W przypadku elementem docelowym jest konkretny .NET Framework, system kompilacji rozpoznaje wszystkie typy używając zestawów odwołań w pakiecie docelowym. W czasie wykonywania moduł ładujący Fusion rozpoznaje te same typy dla zestawów środowiska uruchomieniowego, które zwykle znajdują się w pamięci GAC.

 Jeśli zestawy odwołań nie są dostępne, wtedy system kompilacji rozwiązuje typy zestawów używając zestawów środowiska uruchomieniowego. Ponieważ zestawy środowiska uruchomieniowego w pamięci GAC nie są rozróżniane przez pomocnicze numery wersji, istnieje możliwość, że rozwiązanie zostanie wprowadzone do niewłaściwego zestawu. Może się to zdarzyć gdy na przykład istnieje odwołanie do nowej metody wprowadzonej w .NET Framework w wersji 3.5 podczas gdy wersją docelową jest 3.0 Kompilacja zostanie wykonana pomyślnie, a aplikacja będzie działać na komputerze kompilacji, ale nie będzie działać na komputerze, na którym nie ma zainstalowanej wersji 3.5.

 Pakiet docelowy, który jest teraz dostarczany z zestawem SDK .NET Framework zawiera listę wszystkich zestawów środowiska uruchomieniowego w tej wersji środowiska, nazywaną listą redystrybucyjną (Redist), uniemożliwiającą systemowi kompilacji rozpoznawanie typów w niewłaściwy sposób wersja zestawu.

## <a name="see-also"></a>Zobacz także
- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)