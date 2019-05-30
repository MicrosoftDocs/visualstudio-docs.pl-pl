---
title: Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 601104e484682b7db833f74a3527139ed312e731
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322450"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musi mieć możliwość zlokalizować zestawu biblioteki DLL, można załadować pakietu VSPackage. Możesz znaleźć je na różne sposoby, zgodnie z opisem w poniższej tabeli.

| Metoda | Opis |
| - | - |
| Użyj klucza rejestru bazy kodu. | Klucz CodeBase może służyć do kierowania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] można załadować zestawu pakietu VSPackage z dowolnym w pełni kwalifikowaną ścieżkę. Wartość klucza powinna być ścieżką pliku do biblioteki DLL. Jest to najlepszy sposób mają [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] załadować zestaw pakietów. Ta technika jest czasami określane jako "CodeBase/prywatny instalacji katalogu technika." Podczas rejestracji została przekazana wartość bazy kodu do klasy atrybutów rejestracji za pośrednictwem wystąpienia <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> typu. |
| Umieszczenie biblioteki DLL do **PrivateAssemblies** katalogu. | Umieszczenie zestawu w **PrivateAssemblies** podkatalog [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] katalogu. Zestawy znajdujące się w **PrivateAssemblies** są wykrywane automatycznie, ale nie są widoczne w **Add References** okno dialogowe. Różnica między **PrivateAssemblies** i **PublicAssemblies** jest fakt, że zestawy w **PublicAssemblies** są wymienione **Add References**  okno dialogowe. Jeśli wybierzesz nie należy używać techniki "CodeBase/prywatny katalog instalacji", a następnie należy zainstalować na **PrivateAssemblies** katalogu. |
| Użyj zestawu z silną nazwą i zestawu klucza rejestru. | Klucz zestawu może służyć do kierowania jawnie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] załadować silne silną pakietu VSPackage. Wartość klucza należy silną nazwę zestawu. |
| Umieszczenie biblioteki DLL do **PublicAssemblies** katalogu. | Na koniec zestawu mogą również być umieszczane **PublicAssemblies** podkatalogu. Zestawy znajdujące się w **PublicAssemblies** są wykrywane automatycznie, a następnie pojawi się również w **Add References** okno dialogowe w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Zestawy pakietu VSPackage tylko powinny być umieszczone w **PublicAssemblies** katalogu, jeśli zawierają one zarządzane składniki, które mają być ponownie używane przez innych programistów pakietu VSPackage. Większość zestawów nie spełnia tego kryterium. |

> [!NOTE]
> Na użytek zestawy o silnych nazwach, podpisem wszystkie zależne zestawy. Te zestawy należy również zainstalować w własnego katalogu lub globalnej pamięci podręcznej zestawów (GAC). Chroni to przed powoduje konflikt z zestawów, które mają taką samą nazwę pliku podstawowego, znane jako powiązania weak nazwy.