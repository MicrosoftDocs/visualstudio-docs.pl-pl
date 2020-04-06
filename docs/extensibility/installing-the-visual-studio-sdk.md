---
title: Instalowanie zestawu SDK programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f391708abbd8a9b66f2dfd5aaa6559cb075910d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710346"
---
# <a name="install-the-visual-studio-sdk"></a>Instalowanie zestawu Visual Studio SDK

Zestaw SDK programu Visual Studio (Software Development Kit) jest opcjonalną funkcją w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalowanie pakietu SDK programu Visual Studio w ramach instalacji programu Visual Studio

Aby uwzględnić zestaw SDK programu VS w instalacji programu Visual Studio, zainstaluj obciążenie **programem Visual Studio dotyczące tworzenia rozszerzeń** w obszarze **Inne zestawy narzędzi.** To obciążenie zainstaluje visual studio SDK i niezbędne wymagania wstępne. Instalację można dodatkowo dostroić, wybierając lub odznaczając składniki w widoku **Podsumowanie.**

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalowanie zestawu Visual Studio SDK po zainstalowaniu programu Visual Studio

Aby zainstalować zestaw SDK programu Visual Studio po zakończeniu instalacji programu Visual Studio, uruchom ponownie instalatora programu Visual Studio i wybierz obciążenie **deweloperskie rozszerzenia programu Visual Studio.**

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Instalowanie pakietu SDK programu Visual Studio z rozwiązania

Jeśli otworzysz rozwiązanie z projektem rozszerzalności bez uprzedniego zainstalowania zestawu SDK programu VS, zostanie wyświetlony monit o **zainstalowanie brakującego elementu** dialogowego w celu zainstalowania obciążenia **deweloperskiego rozszerzenia programu Visual Studio:**

![Tworzenie rozszerzeń instalacji](../extensibility/media/install-extension-development.png "Tworzenie rozszerzeń instalacji")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Instalowanie pakietu SDK programu Visual Studio z wiersza polecenia

Podobnie jak w przypadku dowolnego obciążenia lub składnika programu Visual Studio, można również zainstalować obciążenie **deweloperskie rozszerzenia programu Visual Studio** (identyfikator: Microsoft.VisualStudio.Workload.VisualStudioExtension) z wiersza polecenia. Zobacz [Użycie parametrów wiersza polecenia, aby zainstalować program Visual Studio, aby](../install/use-command-line-parameters-to-install-visual-studio.md) uzyskać szczegółowe informacje na temat odpowiednich przełączników wiersza polecenia i ogólnych instrukcji dotyczących określania identyfikatorów obciążenia lub składników.

Należy zauważyć, że należy użyć instalatora programu Visual Studio, który pasuje do zainstalowanej wersji programu Visual Studio. Na przykład jeśli na komputerze jest zainstalowany program Visual Studio Enterprise, należy uruchomić instalator programu Visual Studio Enterprise (*vs_enterprise.exe*).
