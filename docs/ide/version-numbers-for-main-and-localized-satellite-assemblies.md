---
title: Numery wersji dla głównych i zlokalizowanych zestawów satelickich
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1a22978ee432f4de261932808589e92c9738a8b0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880484"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Numery wersji dla głównych i zlokalizowanych zestawów satelickich
<xref:System.Resources.SatelliteContractVersionAttribute> Klasy obsługuje przechowywanie wersji głównej zestawu, który używa zlokalizowane zasoby przy użyciu usługi Resource Manager. Stosowanie <xref:System.Resources.SatelliteContractVersionAttribute> dla aplikacji zestawu głównego pozwala na aktualizowanie i ponowne wdrażanie zestawu bez aktualizowania swoich zestawów satelickich. Na przykład, można użyć <xref:System.Resources.SatelliteContractVersionAttribute> klasy dodatku service pack, który nie wprowadzają nowych zasobów bez ponownego kompilowania lub wdrażania zestawów satelickich. Zlokalizowanych zasobów była dostępna, musi być zgodna wersja kontraktu satelickie zestawu głównego <xref:System.Reflection.AssemblyVersionAttribute> klasy zestawów satelickich. Określ numer wersji dokładnie w <xref:System.Resources.SatelliteContractVersionAttribute>; znaki symboli wieloznacznych, takich jak "*" nie są dozwolone. Aby uzyskać więcej informacji, zobacz [pobierania zasobów](/dotnet/framework/resources/retrieving-resources-in-desktop-apps).

## <a name="update-assemblies"></a>Aktualizowanie zestawów
 <xref:System.Resources.SatelliteContractVersionAttribute> Klasy umożliwia zaktualizowanie głównym zestawie bez konieczności aktualizowania Twojego zestawu satelickiego i na odwrót. Po zaktualizowaniu zestawu głównego, jego numer wersji zestawu jest zmieniany. Jeśli chcesz kontynuować korzystanie z istniejących zestawów satelickich, należy zmienić numer wersji zestawu głównego, ale numer wersji kontraktu satelitarnej pozostaną bez zmian. Na przykład w swojej pierwszej wersji używanej wersji zestawu głównego może być 1.0.0.0. Wersja kontraktu satelitarne i wersji zestawu zestawu satelickiego będzie również 1.0.0.0. Jeśli musisz zaktualizować swojego głównego zestawu z dodatkiem Service Pack, możesz zmienić wersję zestawu do 1.0.0.1, przy jednoczesnym zachowaniu wersja kontraktu satelitarne i wersję zestawu satelickiego jako 1.0.0.0.

 W razie potrzeby można zaktualizować zestawu satelickiego, ale nie głównym zestawie, zmienić <xref:System.Reflection.AssemblyVersionAttribute> zestawu satelickiego. Wraz z zestawem satelickim trzeba będzie wysłać zestaw zasad, z informacją o tym, że Twojego nowego zestawu satelickiego jest zgodna z swoje stare zestawu satelickiego. Aby uzyskać więcej informacji na temat zasad, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

 Poniższy kod przedstawia sposób ustawiania wersja kontraktu satelity. Kod można umieścić w skrypcie kompilacji lub w *AssemblyInfo.vb* lub *AssemblyInfo.cs* pliku.

```vb
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>
```

```csharp
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]
```

## <a name="see-also"></a>Zobacz także

- [Jak środowisko uruchomieniowe lokalizuje zestawy](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [Zestaw atrybutów zestawu](/dotnet/framework/app-domains/set-assembly-attributes)
- [Zabezpieczenia a zlokalizowane zestawy satelickie](../ide/security-and-localized-satellite-assemblies.md)
- [Lokalizowanie aplikacji](../ide/localizing-applications.md)
- [Sprzedawać i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)