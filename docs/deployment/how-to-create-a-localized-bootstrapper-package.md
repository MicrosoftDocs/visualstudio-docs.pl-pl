---
title: Tworzenie zlokalizowanego pakietu programu inicjjącego | Microsoft Docs
description: Dowiedz się, jak utworzyć zlokalizowane wersje pakietu programu inicjjącego w clickOnce, tworząc dwa kolejne pliki dla każdego ustawienia lokalnego.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2a9d1fc91dcb385a9250dde3adb47c0d9553147f
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877718"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Instrukcje: tworzenie zlokalizowanego pakietu programu inicjującego
Po utworzeniu pakietu programu inicjjącego można utworzyć zlokalizowane wersje pakietu programu inicjjącego, tworząc dwa kolejne pliki dla każdego z tych plików: plik postanowień licencyjnych oprogramowania (np. *eula.rtf*) i manifest pakietu (*package.xml*).

 Domyślnie program Visual Studio 2010 zawiera zlokalizowane pakiety programu inicjujące tylko dla wersji .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 i F# Runtime 4.0. Zlokalizowane pakiety dla innych osób inicjujące można utworzyć, wykonując trzy kroki.

1. Utwórz folder o nazwie zgodnie z nazwą ustawienia lokalnego w *folderze \Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages. \\ \<BootstrapperPackageName>*

2. Utwórz plik zawierający postanowienia licencyjne dotyczące oprogramowania dla pakietu programu inicjjącego i umieść go w nowym folderze.

3. Utwórz manifest pakietu o *package.xml*, zaktualizuj ciągi i kulturę i umieść plik w nowym folderze. Jeśli utworzono już program inicjujący Visual Studio w języku docelowym, możesz skopiować plik Visual Studio *package.xml* i zmodyfikować go w tym kroku.

> [!NOTE]
> Jeśli do wdrażania aplikacji używasz projektu Instalatora, możesz zlokalizowane aplikacje, zmieniając **właściwość Lokalizacja.**

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>Aby utworzyć zlokalizowany pakiet programu inicjjącego

1. Utwórz folder o nazwie na tej nazwie.

     Na komputerach 32-bitowych utwórz folder w folderze *\Program Files\Microsoft SDKs\ClickOnce Bootstrapper\Packages. \\ \<BootstrapperPackageName> \\*

     Na komputerach 64-bitowych utwórz folder w folderze *\Program Files (x86)\Microsoft \\ \<BootstrapperPackageName> \\ SDKs\ClickOnce Bootstrapper\Packages.*

     W poniższej tabeli przedstawiono nazwy folderów, których można użyć do dopasowania do danych regionalnych.

    |Regionalne|Nazwa folderu|
    |------------|-----------------|
    |Chiński (uproszczony)|zh-Hans|
    |Chiński (tradycyjny)|zh-Hant|
    |Czeski|Cs|
    |Niemiecki|de|
    |Angielski|en|
    |Hiszpański|es|
    |Francuski|fr|
    |Włoski|it|
    |Koreański|Ko|
    |japoński|ja|
    |Polski|Pl|
    |Portugalski (Brazylia)|pt-BR|
    |Rosyjski|ru|
    |Turecki|Tr|

2. Utwórz plik zawierający postanowienia licencyjne dotyczące oprogramowania dla pakietu programu inicjjącego i umieść go w nowym folderze.

3. Utwórz manifest pakietu o *package.xml* i umieść go w nowym folderze. Aby uzyskać więcej informacji, [zobacz How to: Create a package manifest](../deployment/how-to-create-a-package-manifest.md)( Jak utworzyć manifest pakietu).

4. Zaktualizuj `<Strings>` sekcję manifestu pakietu tak, aby ciągi zawierały prawidłowy język dla danych regionalnych.

5. Zmień wartość `<String Name="Culture">` tak, aby odpowiadała nazwie folderu.

6. Zapisz *package.xml* plik.

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Aby utworzyć pakiet programu inicjujący dla programu .NET Framework 3.5 z dodatkiem Service Pack 1 zlokalizowanego w języku francuskim

1. Utwórz folder o nazwie *fr*. Nazwa folderu musi być dopasowana do nazwy regionalnych.

     Na komputerach 32-bitowych utwórz folder w folderze *\Program Files\Microsoft SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1. \\*

     Na komputerach 64-bitowych utwórz folder w folderze *\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1. \\*

2. Umieść zlokalizowane wersje postanowień licencyjnych oprogramowania w *folderze fr.*

3. Skopiuj *plik \Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* do folderu *fr,* a następnie otwórz plik w Projektancie XML.

4. Zaktualizuj `<Strings>` sekcję manifestu pakietu tak, aby ciągi błędów są w języku francuskim.

5. Zmień wartość `<String Name="Culture">` na *fr*.

6. Zapisz *package.xml* plik.

>[!NOTE]
> Począwszy od wersji Visual Studio 2019 Update 7 pakiety programu inicjujące będą również odnalezione w ścieżce *<VS Install Path> \MSBuild\Microsoft\VisualStudio\BootstrapperPackages.*

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowych pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md)
- [Wstępnie wymagane składniki wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)
- [Instrukcje: tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md)