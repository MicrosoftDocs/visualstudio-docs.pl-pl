---
title: Rozwiązywanie zestawów w czasie projektowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e8f2bc946df5a84b85fc64f513d35c94c98b152
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986077"
---
# <a name="resolve-assemblies-at-design-time"></a>Rozwiązywanie zestawów w czasie projektowania
Po dodaniu odwołania do zestawu za pomocą **.NET** karcie **Dodaj odwołanie** okno dialogowe, punkty odniesienia do pośrednie odwołanie do zestawu, czyli zestaw, który zawiera wszystkie typy i informacje o podpisie, ale niekoniecznie nie zawiera żadnego kodu. **.NET** karcie znajduje się lista zestawów odwołań, które odpowiadają zestawom środowiska uruchomieniowego w .NET Framework. Ponadto Wyświetla listę zestawów odwołań, które odpowiadają zestawom środowiska uruchomieniowego w zarejestrowanych folderach AssemblyFoldersEx używanych przez osoby trzecie.  
  
## <a name="multi-targeting"></a>Wielowersyjność kodu  
 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] pozwala na wybór wersji .NET Framework, która działa albo w Środowisku uruchomieniowym języka wspólnego (CLR) wersja 2 lub wersja 4. Zawierają wersje .NET Framework 2.0, 3.0, 3.5, 4, 4.5 i 4.5.1 i wersji Silverlight 1.0, 2.0 i 3.0. Jeśli zostanie wydana nowa wersja .NET Framework oparta na wersji CLR 2.0 lub wersji 4, Framework może być zainstalowany przy użyciu odpowiedniego pakietu i automatycznie pojawi się jako cel w programie Visual Studio.  
  
## <a name="how-type-resolution-works"></a>Jak wpisać działa rozpoznawanie  
 W czasie wykonywania CLR rozwiązuje typy w zestawie przez wyszukiwanie w pamięci podręcznej GAC, *bin* katalogu i wszelkich ścieżkach sondowania. Jest to obsługiwane przez moduł ładujący fusion. Ale skąd moduł ładujący fusion wie czego szukać? To zależy od rozdzielczości wybranej w czasie projektowania, podczas kompilowania aplikacji.  
  
 Podczas kompilacji, kompilator rozwiązuje typy aplikacji używając zestawów odwołania. W wersjach .NET Framework 2.0, 3.0, 3.5, 4, 4.5 i 4.5.1 zestawy odwołań zainstalować podczas instalacji programu .NET Framework.  
  
 Zestawy odwołania są dostarczane przez pakiet docelowy, który jest dostarczany z odpowiednią wersją .NET Framework SDK. Framework sam w sobie dostarcza tylko zestawy środowiska uruchomieniowego. W celu skompilowania aplikacji należy zainstalować zarówno .NET Framework jak i odpowiadające mu .NET Framework SDK.  
  
 W przypadku elementem docelowym jest konkretny .NET Framework, system kompilacji rozpoznaje wszystkie typy używając zestawów odwołań w pakiecie docelowym. W czasie wykonywania moduł ładujący fusion rozpoznaje te same typy do zestawów środowiska uruchomieniowego, które z reguły są zlokalizowane w GAC.  
  
 Jeśli zestawy odwołań nie są dostępne, wtedy system kompilacji rozwiązuje typy zestawów używając zestawów środowiska uruchomieniowego. Ponieważ zestawy środowiska uruchomieniowego w GAC nie są rozróżniane przez numer wersji pomocniczej, jest możliwe, że zostanie rozpoznany zły zestaw. Może się to zdarzyć gdy na przykład istnieje odwołanie do nowej metody wprowadzonej w .NET Framework w wersji 3.5 podczas gdy wersją docelową jest 3.0 Kompilacja zostanie wykonana pomyślnie, a aplikacja będzie działać na komputerze kompilacji, ale nie będzie działać na komputerze, na którym nie ma zainstalowanej wersji 3.5.  
  
 Pakiet docelowy, który jest teraz dostarczany z .NET Framework SDK zawiera listę wszystkich zestawów środowiska uruchomieniowego w tej wersji środowiska, nazywaną listą redystrybucji (redist) listy, uniemożliwiając system kompilacji rozwiązanie typów nieprawidłowa Wersja zestawu.  
  
## <a name="see-also"></a>Zobacz także  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)