---
title: Programowanie zespołowe rozwiązań pakietu Office
description: Dowiedz się, jak wielu deweloperów może pracować w projekcie pakietu Office w taki sam sposób, jak współpraca w innych projektach programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d30f28b3e97469bc9e0bf921438960206b4f89c0
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845807"
---
# <a name="collaborative-development-of-office-solutions"></a>Programowanie zespołowe rozwiązań pakietu Office
  Wielu deweloperów może pracować nad projektem pakietu Office w taki sam sposób, w jaki współpracują z innymi projektami programu Visual Studio. Program Visual Studio poprawnie lokalizuje instalację Microsoft Office na każdym komputerze, nawet jeśli pakiet Office jest zainstalowany w różnych lokalizacjach. Należy jednak wziąć pod uwagę pewne ważne zagadnienia.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>Właściwości debugowania nie są udostępniane
 Właściwości debugowania nie są współużytkowane przez wielu użytkowników w ramach kontroli źródła. Projekty Visual Basic i Visual C# przechowują właściwości debugowania w pliku specyficznym dla użytkownika (*ProjectName*. vbproj. user lub *ProjectName*. csproj. user), a ten plik nie znajduje się pod kontrolą źródła. Jeśli debugowanie jest więcej niż jedna osoba, każda osoba musi ręcznie wprowadzić właściwości debugowania.

 Jeśli projekt jest przechowywany w udziale sieciowym, a nie w kontroli źródła, należy podjąć pewne dodatkowe kroki, aby umożliwić deweloperom współpracy i przetestowanie zestawu.

## <a name="source-control-requires-checking-out-all-files"></a>Kontrola źródła wymaga wyewidencjonowania wszystkich plików
 W przypadku korzystania z kontroli źródła dla projektów należy wyewidencjonować wszystkie pliki w pliku z kodem w **Eksplorator rozwiązań** (na przykład pliki *ThisDocument*, *ThisWorkbook* lub *ThisAddIn* ) za każdym razem, gdy zmieniany jest plik kodu, nawet pliki, które są domyślnie ukryte. W przypadku wyewidencjonowania tylko pliku z kodem najwyższego poziomu zmiany mogą zostać utracone.

 Po wprowadzeniu zmian zaznacz wszystkie pliki ponownie. Aby uzyskać więcej informacji o plikach ukrytych kodu w projektach, zobacz [projekty pakietu Office w środowisku programu Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="security-for-informal-collaboration-on-a-network"></a>Zabezpieczenia nieformalnej współpracy w sieci
 W przypadku wszystkich rozwiązań na poziomie dokumentu, które znajdują się w lokalizacji sieciowej (na przykład \\ \\ *servername* \\ *ShareName*), w pełni kwalifikowana lokalizacja musi zostać dodana do listy zaufanych folderów w aplikacji Microsoft Office, z którą pracujesz. Wybierz opcję dołączenia podkatalogów w folderze głównym lub w celu dodania folderów debugowania i kompilacji do listy zaufanych folderów. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [Grant Trust to Documents](../vsto/granting-trust-to-documents.md).

 Certyfikaty tymczasowe, które są generowane automatycznie w czasie kompilacji, nie są chronione przez hasła. Certyfikaty zawierają nazwę logowania programisty oraz inne dane osobowe. Po wdrożeniu dostosowań, które są podpisane przez certyfikaty tymczasowe, inne osoby mogą mieć dostęp do tych informacji.

## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
