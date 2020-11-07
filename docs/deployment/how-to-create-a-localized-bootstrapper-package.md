---
title: Tworzenie zlokalizowanego pakietu programu inicjującego | Microsoft Docs
description: Dowiedz się, jak utworzyć zlokalizowane wersje pakietu programu inicjującego w technologii ClickOnce, tworząc dwa więcej plików dla każdego ustawienia regionalnego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 4858a9efdad747293a94563196108d895c40880b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351248"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Instrukcje: tworzenie zlokalizowanego pakietu programu inicjującego
Po utworzeniu pakietu programu inicjującego można utworzyć zlokalizowane wersje pakietu programu inicjującego, tworząc dwa więcej plików dla każdej z ustawień regionalnych: plik warunków licencji oprogramowania (na przykład *EULA. rtf* ) i manifest pakietu ( *package.xml* ).

 Domyślnie program Visual Studio 2010 zawiera zlokalizowane pakiety programu inicjującego tylko dla .NET Framework 4, .NET Framework 4, profilu klienta w języku F 2,0 # oraz środowiska uruchomieniowego F # 4,0. Można utworzyć zlokalizowane pakiety dla innych programów inicjujących, wykonując trzy kroki.

1. Utwórz folder o nazwie po nazwie ustawień regionalnych w *folderze \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ \<BootstrapperPackageName>*.

2. Utwórz plik zawierający postanowienia licencyjne dotyczące oprogramowania dla programu inicjującego i umieść go w nowym folderze.

3. Utwórz manifest pakietu o nazwie *package.xml* , zaktualizuj ciągi i kulturę i umieść plik w nowym folderze. Jeśli utworzono już program inicjujący programu Visual Studio w języku docelowym, możesz skopiować plik programu Visual Studio *package.xml* i zmodyfikować go w tym kroku.

> [!NOTE]
> Jeśli używasz projektu konfiguracji do wdrażania aplikacji, możesz zlokalizować aplikację, zmieniając właściwość **lokalizacji** .

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>Aby utworzyć zlokalizowany pakiet programu inicjującego

1. Utwórz folder o nazwie po nazwie ustawień regionalnych.

     Na komputerach 32-bitowych Utwórz folder w folderze *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ \<BootstrapperPackageName> \\* .

     Na komputerach 64-bitowych Utwórz folder w folderze *\Program Files (86 \\ \<BootstrapperPackageName> \\ ) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* .

     W poniższej tabeli przedstawiono nazwy folderów, których można użyć do dopasowania ustawień regionalnych.

    |Regionalne|Nazwa folderu|
    |------------|-----------------|
    |Chiński (uproszczony)|zh-Hans|
    |Chiński (tradycyjny)|zh-Hant|
    |Czeski|Rejestr|
    |Niemiecki|de|
    |Angielski|en|
    |Hiszpański|es|
    |Francuski|fr|
    |Włoski|it|
    |Koreański|Ko|
    |japoński|ja|
    |Polski|zysków|
    |Portugalski (Brazylia)|pt-BR|
    |Rosyjski|ru|
    |Turecki|zdawczy|

2. Utwórz plik zawierający postanowienia licencyjne dotyczące oprogramowania dla programu inicjującego i umieść go w nowym folderze.

3. Utwórz manifest pakietu o nazwie *package.xml* i umieść go w nowym folderze. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md).

4. Zaktualizuj `<Strings>` sekcję manifestu pakietu, tak aby ciągi były w prawidłowym języku dla ustawień regionalnych.

5. Zmień wartość tak, `<String Name="Culture">` aby odpowiadała nazwie folderu.

6. Zapisz plik *package.xml* .

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Aby utworzyć pakiet programu inicjującego dla .NET Framework 3,5 dodatek Service Pack 1 zlokalizowany w języku francuskim

1. Utwórz folder o nazwie *fr*. Nazwa folderu musi być zgodna z nazwą ustawień regionalnych.

     Na komputerach 32-bitowych Utwórz folder w folderze *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1 \\* .

     Na komputerach 64-bitowych Utwórz folder w folderze *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1 \\* .

2. Umieść zlokalizowaną wersję postanowień licencyjnych dotyczących oprogramowania w folderze *fr* .

3. Skopiuj plik *\Program Files (x86) \microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* do folderu *fr* i Otwórz plik w Projektancie XML.

4. Zaktualizuj `<Strings>` sekcję manifestu pakietu, aby ciągi błędów były w języku francuskim.

5. Zmień `<String Name="Culture">` wartość na *fr*.

6. Zapisz plik *package.xml* .

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowych pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md)
- [Wstępnie wymagane składniki wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)
- [Instrukcje: tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md)