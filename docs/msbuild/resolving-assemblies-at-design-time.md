---
title: Rozwiązywanie zestawów w czasie projektowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69f5ba2627e2d659665fa0bd3fbf706f9cad5573
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632566"
---
# <a name="resolve-assemblies-at-design-time"></a>Rozwiązywanie problemów z złożeniami w czasie projektowania

Po dodaniu odwołania do złożenia za pośrednictwem karty **.NET** okna dialogowego **Dodaj odwołanie,** punkt odniesienia do zestawu odniesienia pośredniego; oznacza to, że zestaw, który zawiera wszystkie informacje o typie i podpisie, ale który nie musi zawierać żadnego kodu. Karta **.NET** zawiera listę zestawów odwołań, które odpowiadają zestawom środowiska wykonawczego w ramach .NET Framework. Ponadto wyświetla listę zestawów odwołań, które odpowiadają zestawom środowiska wykonawczego w zarejestrowanych folderach AssemblyFoldersEx, które są używane przez osoby trzecie.

## <a name="multi-targeting"></a>Kierowanie wielokrotne

 Program Visual Studio umożliwia docelowe wersje programu .NET Framework, które są uruchamiane w wielu wersjach programu .NET Framework. Po wydaniu nowej wersji programu .NET Framework framework można zainstalować za pomocą pakietu docelowego i automatycznie pojawi się jako miejsce docelowe w programie Visual Studio.

## <a name="how-type-resolution-works"></a>Jak działa rozdzielczość typu

 W czasie wykonywania CLR rozpoznaje typy w zestawie, patrząc w GAC, katalogu *bin* i we wszystkich ścieżkach sondowania. Jest to obsługiwane przez moduł ładujący fusion. Ale skąd moduł ładujący fusion wie czego szukać? To zależy od rozdzielczości wykonanej w czasie projektowania, kiedy aplikacja jest zbudowana.

 Podczas kompilacji, kompilator rozwiązuje typy aplikacji używając zestawów odwołania. W programach .NET Framework w wersjach 2.0, 3.0, 3.5, 4,5 i 4.5.1 zestawy odwołań są instalowane po zainstalowaniu programu .NET Framework.

 Zestawy odwołania są dostarczane przez pakiet docelowy, który jest dostarczany z odpowiednią wersją .NET Framework SDK. Framework sam w sobie dostarcza tylko zestawy środowiska uruchomieniowego. W celu skompilowania aplikacji należy zainstalować zarówno .NET Framework jak i odpowiadające mu .NET Framework SDK.

 W przypadku elementem docelowym jest konkretny .NET Framework, system kompilacji rozpoznaje wszystkie typy używając zestawów odwołań w pakiecie docelowym. W czasie wykonywania moduł ładujący fuzji rozpoznaje te same typy do zestawów środowiska wykonawczego, które zazwyczaj znajdują się w pliku GAC.

 Jeśli zestawy odwołań nie są dostępne, wtedy system kompilacji rozwiązuje typy zestawów używając zestawów środowiska uruchomieniowego. Ponieważ zestawy środowiska wykonawczego w pliku GAC nie są rozróżniane przez pomocnicze numery wersji, jest możliwe, że rozdzielczość zostanie wykonana do niewłaściwego zestawu. Może się to zdarzyć gdy na przykład istnieje odwołanie do nowej metody wprowadzonej w .NET Framework w wersji 3.5 podczas gdy wersją docelową jest 3.0 Kompilacja zostanie wykonana pomyślnie, a aplikacja będzie działać na komputerze kompilacji, ale nie będzie działać na komputerze, na którym nie ma zainstalowanej wersji 3.5.

 Pakiet kierowania, który jest teraz dostarczany z zestawem .NET Framework SDK, zawiera listę wszystkich zestawów środowiska wykonawczego w tej wersji programu Framework, zwaną listą redystrybucji (redist), uniemożliwiając systemowi kompilacji rozpoznawanie typów z niewłaściwym wersji zestawu.

## <a name="see-also"></a>Zobacz też
- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
