---
title: Instalowanie zestawu Visual Studio SDK | Microsoft Docs
description: Dowiedz się więcej na temat opcji instalacji zestawu Visual Studio Software Development Kit, w tym podczas instalacji programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5b0d239c2280362b45c085448437b15bd8ddfe8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869534"
---
# <a name="install-the-visual-studio-sdk"></a>Instalowanie zestawu Visual Studio SDK

Visual Studio SDK (Software Development Kit) to opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalowanie zestawu Visual Studio SDK w ramach instalacji programu Visual Studio

Aby uwzględnić zestaw SDK programu VS w instalacji programu Visual Studio, należy zainstalować obciążenie **programowanie rozszerzeń programu Visual Studio** w obszarze **inne zestawy narzędzi**. To obciążenie spowoduje zainstalowanie zestawu Visual Studio SDK i wymaganych wymagań wstępnych. Instalację można dostosowywać, zaznaczając lub usuwając zaznaczenie składników z widoku **podsumowania** .

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalowanie zestawu Visual Studio SDK po zainstalowaniu programu Visual Studio

Aby zainstalować zestaw Visual Studio SDK po zakończeniu instalacji programu Visual Studio, uruchom ponownie Instalatora programu Visual Studio i wybierz obciążenie **programowanie rozszerzenia programu Visual Studio** .

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Instalowanie zestawu Visual Studio SDK z rozwiązania

Jeśli otworzysz rozwiązanie przy użyciu projektu rozszerzalności bez wcześniejszego zainstalowania zestawu SDK programu VS, zostanie wyświetlony monit o zainstalowanie **brakującej funkcji** okna dialogowego umożliwiającej zainstalowanie obciążenia **programistycznego rozszerzenia programu Visual Studio** :

![Zainstaluj programowanie rozszerzeń](../extensibility/media/install-extension-development.png "Zainstaluj programowanie rozszerzeń")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Instalowanie zestawu SDK programu Visual Studio z poziomu wiersza polecenia

Podobnie jak w przypadku dowolnego obciążenia lub składnika programu Visual Studio, można również zainstalować obciążenie **programowanie rozszerzeń programu Visual Studio** (Identyfikator: Microsoft. VisualStudio. obciążeni. VisualStudioExtension) w wierszu polecenia. Zobacz [Używanie parametrów wiersza polecenia, aby zainstalować program Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) , aby uzyskać szczegółowe informacje na temat odpowiednich przełączników wiersza polecenia i ogólnych instrukcji dotyczących określania obciążeń lub identyfikatorów składników.

Należy pamiętać, że należy użyć Instalatora programu Visual Studio, który jest zgodny z zainstalowaną wersją programu Visual Studio. Na przykład jeśli na komputerze zainstalowano Visual Studio Enterprise, należy uruchomić Instalatora Visual Studio Enterprise (*vs_enterprise.exe*).
