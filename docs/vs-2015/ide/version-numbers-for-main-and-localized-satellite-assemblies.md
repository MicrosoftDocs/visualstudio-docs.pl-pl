---
title: Numery wersji dla głównych i zlokalizowanych zestawów satelickich | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa064d875d5354ac4ae1fc5fdd8493c5efbbee01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663054"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Numery wersji dla głównych i zlokalizowanych zestawów satelickich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Resources.SatelliteContractVersionAttribute>Klasa zapewnia obsługę przechowywania wersji dla zestawu głównego, który używa zlokalizowanych zasobów za pomocą usługi Resource Manager. Zastosowanie <xref:System.Resources.SatelliteContractVersionAttribute> do głównego zestawu aplikacji umożliwia zaktualizowanie i ponowne wdrożenie zestawu bez aktualizowania zestawów satelickich. Można na przykład użyć <xref:System.Resources.SatelliteContractVersionAttribute> klasy z dodatkiem Service Pack, która nie wprowadza nowych zasobów bez konieczności ponownego kompilowania i wdrażania zestawów satelickich. Aby zlokalizowane zasoby były dostępne, wersja kontraktu satelitarnego głównego zestawu musi być zgodna z <xref:System.Reflection.AssemblyVersionAttribute> klasą zestawów satelickich. Należy określić dokładny numer wersji w <xref:System.Resources.SatelliteContractVersionAttribute> ; symbole wieloznaczne, takie jak "*", są niedozwolone. Aby uzyskać więcej informacji, zobacz artykuł [pobieranie zasobów](https://msdn.microsoft.com/library/eca16922-1c46-4f68-aefe-e7a12283641f).

## <a name="updating-assemblies"></a>Aktualizowanie zestawów
 <xref:System.Resources.SatelliteContractVersionAttribute>Klasa umożliwia zaktualizowanie głównego zestawu bez konieczności aktualizowania zestawu satelitarnego lub na odwrót. Gdy główny zestaw zostanie zaktualizowany, jego numer wersji zestawu zostanie zmieniony. Jeśli chcesz kontynuować korzystanie z istniejących zestawów satelickich, Zmień numer wersji zestawu głównego, ale pozostaw numer wersji kontraktu satelitarnego. Przykładowo w pierwszej wersji zestawu głównego można przystąpić do wersji 1.0.0.0. Wersja kontraktu satelickiego i wersja zestawu satelickiego będą również 1.0.0.0. Jeśli musisz zaktualizować główny zestaw dla dodatku Service Pack, możesz zmienić wersję zestawu na 1.0.0.1, pozostawiając wersję kontraktu satelity i wersję zestawu satelitarnego jako 1.0.0.0.

 Jeśli trzeba zaktualizować zestaw satelicki, ale nie zestaw główny, zmienisz <xref:System.Reflection.AssemblyVersionAttribute> zestaw satelity. Wraz z zestawem satelickim konieczne będzie dostarczenie zestawu zasad, który stwierdza, że nowy zestaw satelicki jest zgodny ze starym zestawem satelickim. Aby uzyskać więcej informacji na temat zasad, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).

 Poniższy kod przedstawia sposób ustawienia wersji kontraktu satelity. Kod można umieścić w skrypcie kompilacji lub w pliku AssemblyInfo. vb lub AssemblyInfo.cs.

```vb
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>

```

```csharp
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]
```

## <a name="see-also"></a>Zobacz też
 [Jak środowisko uruchomieniowe lokalizuje zestawy](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34) [atrybutów zestawu](https://msdn.microsoft.com/library/36a98a81-b5b5-4c19-912a-11f91eff7f4e) [Security i zlokalizowanych zestawów satelickich](../ide/security-and-localized-satellite-assemblies.md) , które [lokalizują aplikacje](../ide/localizing-applications.md) [globalizacji i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)
