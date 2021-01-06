---
title: Określanie lokalizacji pliku pakietu VSPackage w usłudze VS Shell | Microsoft Docs
description: Dowiedz się, jak można sprawić, aby program Visual Studio mógł zlokalizować bibliotekę DLL zestawu, aby załadować pakietu VSPackage.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e59bea4894d6b0014542ea2a32bf6c73bc8d797c
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877861"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musi być w stanie zlokalizować bibliotekę DLL zestawu, aby załadować pakietu VSPackage. Można go zlokalizować na różne sposoby, zgodnie z opisem w poniższej tabeli.

| Metoda | Opis |
| - | - |
| Użyj klucza rejestru CodeBase. | Klucz CodeBase może służyć do kierowania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zestawu pakietu VSPackage z dowolnej w pełni kwalifikowanej ścieżki pliku. Wartością klucza powinna być ścieżka do pliku DLL. Jest to najlepszy sposób na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] załadowanie zestawu pakietów. Ta technika jest czasami nazywana techniką "bazowa baza kodu/prywatny katalog instalacji". Podczas rejestracji wartość bazowej bazy danych jest przenoszona do klas atrybutów rejestracji za pomocą wystąpienia <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> typu. |
| Umieść bibliotekę DLL w katalogu **PrivateAssemblies** . | Umieść zestaw w podkatalogu **PrivateAssemblies** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] katalogu. Zestawy znajdujące się w **PrivateAssemblies** są wykrywane automatycznie, ale nie są widoczne w oknie dialogowym **Dodaj odwołania** . Różnica między **PrivateAssemblies** i **PublicAssemblies** polega na tym, że zestawy w **PublicAssemblies** są wyliczane w oknie dialogowym **Dodaj odwołania** . Jeśli nie zostanie użyta technika "bazowa baza/katalog instalacji prywatnej", należy zainstalować program w katalogu **PrivateAssemblies** . |
| Użyj zestawu o silnej nazwie i klucza rejestru zestawu. | Za pomocą klucza zestawu można jawnie skierować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do załadowania silnie nazwanego zestawu pakietu VSPackage. Wartość klucza powinna być silną nazwą zestawu. |
| Umieść bibliotekę DLL w katalogu **PublicAssemblies** . | Na koniec zestaw można również umieścić w podkatalogu **PublicAssemblies** . Zestawy znajdujące się w **PublicAssemblies** są wykrywane automatycznie i pojawią się w oknie dialogowym **Dodaj odwołania** w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .<br /><br /> Zestawy pakietu VSPackage powinny być umieszczane w katalogu **PublicAssemblies** , jeśli zawierają składniki zarządzane, które mają być ponownie używane przez innych deweloperów pakietu VSPackage. Większość zestawów nie spełnia tego kryterium. |

> [!NOTE]
> Używaj podpisanych zestawów o silnych nazwach dla wszystkich zestawów zależnych. Te zestawy należy również zainstalować we własnym katalogu lub w globalnej pamięci podręcznej zestawów (GAC). Chroni przed konfliktami z zestawami, które mają taką samą nazwę pliku podstawowego, jak powiązanie słabej nazwy.
