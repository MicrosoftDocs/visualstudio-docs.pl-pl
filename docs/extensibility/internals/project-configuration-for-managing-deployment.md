---
title: Konfiguracja projektu do zarządzania wdrożeniem | Microsoft Docs
description: Dowiedz się więcej o wdrażaniu w oczekiwanej lokalizacji na potrzeby debugowania i instalacji, a dwa sposoby, w których program Visual Studio obsługuje projekty obsługujące wdrożenie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 589403f126a4fd614911c1deb99e9acd32d1ec7d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074421"
---
# <a name="project-configuration-for-managing-deployment"></a>Konfigurowanie projektu do zarządzania wdrożeniem
Wdrożenie to czynność fizycznej przenoszenia elementów wyjściowych z procesu kompilacji do oczekiwanej lokalizacji na potrzeby debugowania i instalacji. Na przykład aplikacja sieci Web może być skompilowana na komputerze lokalnym, a następnie umieszczana na serwerze.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Program obsługuje dwa sposoby, w których projekty mogą być uwzględnione we wdrożeniu:

- W ramach procesu wdrażania.

- Jako Menedżer procesu wdrażania.

  Przed wdrożeniem rozwiązań należy najpierw dodać projekt wdrożenia w celu skonfigurowania opcji wdrażania. Jeśli projekt wdrożenia jeszcze nie istnieje, zostanie wyświetlony monit o jego utworzenie, gdy wybierzesz opcję **Wdróż rozwiązanie** z menu **kompilacja** lub kliknij prawym przyciskiem myszy rozwiązanie. Kliknięcie przycisku **tak** spowoduje otwarcie okna dialogowego **Dodawanie nowego projektu** z wybranym projektem **Kreatora wdrażania zdalnego** .

  Kreator zdalnego wdrażania monituje o typ aplikacji (Windows lub Web), grupy danych wyjściowych projektu do uwzględnienia, wszelkie dodatkowe pliki, które mają zostać uwzględnione, oraz komputer zdalny, na którym ma zostać wdrożony. Ostatnia strona kreatora wyświetla podsumowanie wybranych opcji.

  Projekty, które są podmiotem procesu wdrażania, tworzą elementy wyjściowe, które muszą zostać przeniesione do alternatywnego środowiska. Te elementy wyjściowe są opisane jako parametry <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interfejsu, którego głównym celem jest umożliwienie projektom grupowania danych wyjściowych. Aby uzyskać więcej informacji dotyczących implementacji programu `IVsProjectCfg2` , zobacz [Konfiguracja projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).

  Projekty wdrażania, które zarządzają procesem wdrażania, włączają polecenie Wdróż i reagują, gdy to polecenie jest zaznaczone. Projekty wdrożenia implementują <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfejs do wykonania wdrożenia i wykonują wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interfejsu w celu raportowania zdarzeń stanu wdrożenia.

  Konfiguracje mogą określać zależności, które wpływają na operacje kompilowania lub wdrażania. Zależności kompilacji lub wdrożenia to projekty, które muszą zostać skompilowane lub wdrożone przed lub po skompilowaniu lub zakończeniu konfiguracji. Zależności kompilacji między projektami są opisane w <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interfejsie i wdrażają zależności z <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfejsem. Aby uzyskać więcej informacji, zobacz [Konfiguracja projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
