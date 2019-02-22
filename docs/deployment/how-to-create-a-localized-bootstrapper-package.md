---
title: 'Instrukcje: Tworzenie zlokalizowanego pakietu programu inicjującego | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbd9aab09d4972e5fe9c1784aed7cadf15c3db4c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611168"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Instrukcje: Tworzenie zlokalizowanego pakietu programu inicjującego
Po utworzeniu pakietu programu inicjującego, tworząc dwie więcej plików dla poszczególnych ustawień regionalnych, można utworzyć zlokalizowane wersje pakietu programu inicjującego: postanowienia licencyjne dotyczące oprogramowania plików (takich jak *eula.rtf*) oraz manifest pakietu (*package.xml*).

 Domyślnie program Visual Studio 2010 zawiera zlokalizowane pakiety programu inicjującego tylko dla .NET Framework 4, .NET Framework 4 Client Profile F# środowiska uruchomieniowego w wersji 2.0 i F# 4.0 środowiska uruchomieniowego. Zlokalizowane pakiety dla innych programów inicjujących można utworzyć, wykonując trzy kroki.

1.  Utwórz folder o nazwie po nazwie ustawień regionalnych *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >*.

2.  Utwórz plik, który zawiera postanowienia licencyjne dotyczące oprogramowania pakietu programu inicjującego i umieścić go w nowym folderze.

3.  Tworzenie manifestu pakietu o nazwie *package.xml*, zaktualizuj ciągi i kultury i umieścić ten plik w nowym folderze. Jeśli utworzono już program inicjujący programu Visual Studio w języku docelowym, możesz skopiować programu Visual Studio *package.xml* plik i zmodyfikować go w tym kroku.

> [!NOTE]
>  Jeśli używasz projektów Instalatora do wdrażania aplikacji, można zlokalizować aplikację, zmieniając **lokalizacji** właściwości.

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>Aby utworzyć zlokalizowanego pakietu programu inicjującego

1.  Utwórz folder o nazwie po nazwie ustawień regionalnych.

     Na komputerach 32-bitowych utworzone w folderze *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >\\*  folderu.

     Na komputerach 64-bitowych utworzone w folderze *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >\\*  folderu.

     W poniższej tabeli przedstawiono nazwy folderów, które służy do dopasowania ustawień regionalnych.

    |Regionalne|Nazwa folderu|
    |------------|-----------------|
    |Chiński uproszczony|zh-Hans|
    |Chiński (tradycyjny)|zh-Hant|
    |czeski|cs|
    |niemiecki|Niemcy|
    |Angielski|pl|
    |Hiszpański|es|
    |Francuski|fr|
    |Włoski|go|
    |koreański|ko|
    |japoński|ja|
    |polski|pl|
    |portugalski (Brazylia)|pt-BR|
    |Rosyjski|ru|
    |turecki|tr|

2.  Utwórz plik, który zawiera postanowienia licencyjne dotyczące oprogramowania pakietu programu inicjującego i umieścić go w nowym folderze.

3.  Tworzenie manifestu pakietu o nazwie *package.xml* i umieścić go w nowym folderze. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md).

4.  Aktualizacja `<Strings>` części pakietu manifestu, tak aby ciągi znajdują się w prawidłowym języku dla ustawień regionalnych.

5.  Zmiana `<String Name="Culture">` wartość jest zgodna z nazwą folderu.

6.  Zapisz *package.xml* pliku.

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Aby utworzyć pakiet programu inicjującego dla programu .NET Framework 3.5 Service Pack 1 zlokalizowane w języku francuskim

1.  Utwórz folder o nazwie *fr*. Nazwa folderu musi odpowiadać nazwie ustawień regionalnych.

     Na komputerach 32-bitowych utworzone w folderze *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*  folderu.

     Na komputerach 64-bitowych utworzone w folderze *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*  folderu.

2.  Umieść zlokalizowaną wersję postanowienia licencyjne dotyczące oprogramowania do *fr* folderu.

3.  Kopiuj *\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml pliki (x86) \Program* plik *fr* folder, a następnie otwórz plik w Projektancie XML.

4.  Aktualizacja `<Strings>` sekcji pakietu manifestu, tak aby były ciągi błędów w języku francuskim.

5.  Zmiana `<String Name="Culture">` wartość *fr*.

6.  Zapisz *package.xml* pliku.

## <a name="see-also"></a>Zobacz także
- [Tworzenie niestandardowych pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md)
- [Wstępnie wymagane składniki wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)
- [Instrukcje: Tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md)