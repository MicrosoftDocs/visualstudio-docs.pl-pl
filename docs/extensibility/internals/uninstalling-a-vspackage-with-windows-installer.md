---
title: Odinstalowywanie pakietu VSPackage za pomocą Instalatora Windows | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fee88e895d40d42114eaf53422503524594b485f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704277"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Odinstalowywanie pakietów VSPackage przy użyciu Instalatora Windows
W przeważającej części Instalator Windows może odinstalować vsPackage tylko przez "cofanie" co zrobił, aby zainstalować VSPackage. Akcje niestandardowe omówione w [poleceniach, które muszą być uruchamiane po instalacji,](../../extensibility/internals/commands-that-must-be-run-after-installation.md) muszą być również uruchamiane po odinstalowaniu. Ponieważ wywołania devenv.exe występują tuż przed installFinalize standardowej akcji zarówno instalacji i dezinstalacji, CustomAction i InstallExecuteSequence wpisy tabeli służyć obu przypadkach.

> [!NOTE]
> Uruchom `devenv /setup` po odinstalowaniu pakietu MSI.

 Zgodnie z ogólną zasadą, jeśli dodasz akcje niestandardowe do pakietu Instalatora Windows, należy obsługiwać te akcje podczas dezinstalacji i wycofywania. Jeśli na przykład dodasz akcje niestandardowe do samodzielnego rejestrowania pakietu VSPackage, należy również dodać akcje niestandardowe, aby go wyrejestrować.

> [!NOTE]
> Użytkownik może zainstalować pakiet VSPackage, a następnie odinstalować wersje, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] z którymi jest zintegrowany. Dezinstalacja vspackage działa w tym scenariuszu, eliminując akcje niestandardowe, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]które uruchamiają kod z zależnościami na .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Obsługa warunków uruchamiania w czasie odinstalowywania
 Akcja standardowa LaunchConditions odczytuje wiersze tabeli LaunchCondition, aby wyświetlić komunikaty o błędach, jeśli warunki nie są spełnione. Ponieważ warunki uruchamiania są zazwyczaj używane w celu zapewnienia, że wymagania systemowe są spełnione, `NOT Installed`zazwyczaj można pominąć warunki uruchamiania podczas dezinstalacji, dodając warunek, do wiersza LaunchConditions tabeli LaunchCondition.

 Alternatywą jest `OR Installed` dodanie do warunków uruchamiania, które nie są ważne podczas dezinstalacji. Dzięki temu warunek będzie zawsze spełniony podczas dezinstalacji i dlatego nie będzie wyświetlany komunikat o błędzie warunku uruchamiania.

> [!NOTE]
> `Installed`jest właściwością Instalatora Windows ustawia, gdy wykryje, że vsPackage został już zainstalowany w systemie.

## <a name="see-also"></a>Zobacz też
- [Instalator Windows](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md)
