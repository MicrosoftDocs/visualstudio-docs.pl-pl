---
title: Określanie lokalizacji pliku VSPackage do powłoki VS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f112da4e79bff06d12472f0af7a3fe47b2f25da4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704975"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]musi być w stanie zlokalizować bibliotekę DLL zestawu, aby załadować VSPackage. Można go zlokalizować na różne sposoby, zgodnie z opisem w poniższej tabeli.

| Metoda | Opis |
| - | - |
| Użyj klucza rejestru CodeBase. | Klucz CodeBase może służyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do bezpośredniego ładowania zestawu VSPackage z dowolnej ścieżki pliku w pełni kwalifikowany. Wartość klucza powinna być ścieżką pliku do biblioteki DLL. Jest to najlepszy sposób, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] załadować zestaw pakietów. Ta technika jest czasami określana jako "CodeBase/private installation directory technique". Podczas rejestracji wartość codebase jest przekazywana do klas atrybutów <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> rejestracji za pośrednictwem wystąpienia typu. |
| Umieść bibliotekę DLL w katalogu **PrivateAssemblies.** | Umieść zestaw w podkatalogu **PrivateAssemblies** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] katalogu. Zestawy znajdujące się w **privateAssemblies** są wykrywane automatycznie, ale nie są widoczne w oknie dialogowym **Dodawanie odwołań.** Różnica między **PrivateAssemblies** i **PublicAssemblies** jest, że zestawy w **PublicAssemblies** są wyliczone w oknie dialogowym **Dodawanie odwołań.** Jeśli nie chcesz używać techniki "CodeBase/private installation directory", należy zainstalować w katalogu **PrivateAssemblies.** |
| Użyj zestawu o silnej nazwie i klucza rejestru zestawu. | Klucz zestawu może służyć jawnie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bezpośrednie załadować silne nazwie VSPackage zestawu. Wartość klucza powinna być silną nazwą zestawu. |
| Umieść bibliotekę DLL w katalogu **PublicAssemblies.** | Na koniec zestaw można również umieścić w **publicassemblies** podkatalogu. Zestawy znajdujące się w **publicassemblies** są wykrywane automatycznie i pojawią [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]się również w oknie dialogowym **Dodawanie odwołań** w pliku .<br /><br /> VsPackage zestawy powinny być umieszczane w katalogu **PublicAssemblies** tylko wtedy, gdy zawierają składniki zarządzane, które są przeznaczone do ponownego użytku przez innych deweloperów VSPackage. Większość zestawów nie spełnia tego kryterium. |

> [!NOTE]
> Użyj silnej nazwy, podpisane zestawy dla wszystkich zestawów zależnych. Zestawy te powinny być również zainstalowane we własnym katalogu lub globalnej pamięci podręcznej zestawów (GAC). Chroni to przed konfliktami z zestawami, które mają taką samą nazwę pliku podstawowego, znany jako słabe-name powiązania.
