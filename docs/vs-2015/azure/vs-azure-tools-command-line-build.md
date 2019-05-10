---
title: Kompilacji wiersza polecenia platformy Azure | Dokumentacja firmy Microsoft
description: Kompilacji wiersza polecenia platformy Azure
author: ghogen
manager: jillfra
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: 8c96713a06c66fe34e34417e9e8595ba07e50485
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62989819"
---
# <a name="building-azure-projects-from-the-command-line"></a>Tworzenie projektów systemu Azure z poziomu wiersza polecenia
Korzystając z aparatu Microsoft Build Engine (MSBuild), można tworzyć produktów w środowisku laboratorium kompilacji, których nie zainstalowano programu Visual Studio. Program MSBuild używa formatu XML, pliki projektu, czyli rozszerzalne i w pełni obsługiwane przez firmę Microsoft. Przy użyciu formatu pliku MSBuild, można opisać co elementy muszą być zbudowane dla co najmniej jeden platformach i konfiguracjach.

Można również uruchomić program MSBuild w wierszu polecenia, a w tym temacie opisano podejście. Przez ustawienie właściwości w wierszu polecenia, można utworzyć określonej konfiguracji projektu. Podobnie można również zdefiniować obiektów docelowych, które kompilacje programu MSBuild. Aby uzyskać więcej informacji na temat parametrów wiersza polecenia i programu MSBuild, zobacz [odwołanie do wiersza polecenia MSBuild](https://msdn.microsoft.com/library/ms164311.aspx).

## <a name="msbuild-parameters"></a>Parametry programu MSBuild
Najprostszym sposobem, aby utworzyć pakiet jest uruchamiają program MSBuild z `/t:Publish` opcji. Domyślnie to polecenie tworzy katalog w odniesieniu do folderu głównego projektu, taki jak `<ProjectDirectory>\bin\Configuration\app.publish\`. Podczas tworzenia projektu platformy Azure są generowane dwa pliki: plik pakietu wraz z towarzyszącym pliku konfiguracji:

* Plik pakietu (`project.cspkg`)
* Plik konfiguracji (`ServiceConfiguration.TargetProfile.cscfg`)

Domyślnie każdy projekt platformy Azure zawiera jeden plik konfiguracji usługi dla lokalnych kompilacji (debugowanie) i inny wpis dla kompilacji w chmurze (przejściowych lub produkcyjnych). Można jednak dodać lub usunąć pliki konfiguracji usługi, stosownie do potrzeb. W przypadku tworzenia pakietów w programie Visual Studio, zostanie wyświetlony monit plik konfiguracji usługi, który obejmujący wraz z pakietu. Podczas tworzenia pakietu przy użyciu programu MSBuild, domyślnie znajduje się lokalnego pliku konfiguracji usługi. Aby dołączyć inny plik konfiguracji usługi, należy ustawić `TargetProfile` właściwości polecenia MSBuild (`MSBuild /t:Publish /p:TargetProfile=ProfileName`).

Jeśli chcesz używać alternatywny katalog do zapisanego pakietu i pliki konfiguracyjne, Ustaw ścieżkę przy użyciu `/p:PublishDir=Directory\` opcji, w tym końcowe separator ukośnika odwrotnego.

## <a name="next-steps"></a>Następne kroki
Po utworzeniu pakietu, można wdrożyć ją na platformie Azure.