---
title: Kompilacja w wierszu polecenia dla platformy Azure | Microsoft Docs
description: Kompilacja w wierszu polecenia dla platformy Azure
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62989819"
---
# <a name="building-azure-projects-from-the-command-line"></a>Tworzenie projektów platformy Azure z poziomu wiersza polecenia
Korzystając z Microsoft Build Engine (MSBuild), można tworzyć produkty w środowiskach kompilacji, w których nie zainstalowano programu Visual Studio. MSBuild używa formatu XML dla plików projektu, które są rozszerzalne i w pełni obsługiwane przez firmę Microsoft. Korzystając z formatu pliku MSBuild, można opisać, jakie elementy muszą zostać skompilowane dla jednej lub kilku platform i konfiguracji.

Program MSBuild można również uruchomić w wierszu polecenia, a w tym temacie opisano to podejście. Ustawiając właściwości w wierszu polecenia, można utworzyć określone konfiguracje projektu. Analogicznie można także zdefiniować cele kompilacji MSBuild. Aby uzyskać więcej informacji na temat parametrów wiersza polecenia i programu MSBuild, zobacz [Dokumentacja wiersza polecenia programu MSBuild](https://msdn.microsoft.com/library/ms164311.aspx).

## <a name="msbuild-parameters"></a>Parametry programu MSBuild
Najprostszym sposobem utworzenia pakietu jest uruchomienie programu MSBuild z `/t:Publish` opcją. Domyślnie to polecenie tworzy katalog w odniesieniu do folderu głównego projektu, na przykład `<ProjectDirectory>\bin\Configuration\app.publish\` . Podczas kompilowania projektu platformy Azure generowane są dwa pliki: sam plik pakietu i towarzyszący plik konfiguracji:

* Plik pakietu ( `project.cspkg` )
* Plik konfiguracji ( `ServiceConfiguration.TargetProfile.cscfg` )

Domyślnie każdy projekt platformy Azure zawiera jeden plik konfiguracji usługi dla kompilacji lokalnych (debugowania) i drugi dla kompilacji w chmurze (przemieszczanie lub produkcja). Można jednak dodać lub usunąć pliki konfiguracji usługi zgodnie z wymaganiami. Gdy tworzysz pakiet w programie Visual Studio, zostanie wyświetlony monit o plik konfiguracji usługi, który ma zostać uwzględniony wraz z pakietem. W przypadku kompilowania pakietu przy użyciu programu MSBuild domyślnie jest uwzględniany plik konfiguracji usługi lokalnej. Aby dołączyć inny plik konfiguracji usługi, należy ustawić `TargetProfile` Właściwość polecenia MSBuild ( `MSBuild /t:Publish /p:TargetProfile=ProfileName` ).

Jeśli chcesz użyć alternatywnego katalogu dla przechowywanych pakietów i plików konfiguracji, Ustaw ścieżkę przy użyciu `/p:PublishDir=Directory\` opcji, łącznie z końcowym separatorem ukośnika odwrotnego.

## <a name="next-steps"></a>Następne kroki
Po skompilowaniu pakietu można wdrożyć go na platformie Azure.