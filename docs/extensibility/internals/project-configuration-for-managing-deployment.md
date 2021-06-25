---
title: Konfiguracja projektu do zarządzania wdrażaniem | Microsoft Docs
description: Dowiedz się więcej na temat wdrażania w oczekiwanej lokalizacji na potrzeby debugowania i instalacji oraz dwóch sposobów Visual Studio projektów, które obsługują wdrożenie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c6077665ccc3bbe5f87b91a1d2fc5636e08539d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899904"
---
# <a name="project-configuration-for-managing-deployment"></a>Konfigurowanie projektu do zarządzania wdrożeniem
Wdrożenie jest czynnością fizycznego przenoszenia elementów wyjściowych z procesu kompilacji do oczekiwanej lokalizacji na potrzeby debugowania i instalacji. Na przykład aplikacja internetowa może zostać s zbudowana na komputerze lokalnym, a następnie umieszczona na serwerze.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje dwa sposoby, w jakie projekty mogą być zaangażowane we wdrażanie:

- Jako temat procesu wdrażania.

- Jako menedżer procesu wdrażania.

  Przed wdrożeniem rozwiązań należy najpierw dodać projekt wdrożenia, aby skonfigurować opcje wdrażania. Jeśli projekt wdrażania jeszcze nie istnieje, zostanie pytanie, czy  chcesz go utworzyć po wybraniu pozycji Wd wdrażaj rozwiązanie z menu **Kompilacja** lub kliknięciu rozwiązania prawym przyciskiem myszy. Kliknięcie **przycisku Tak** powoduje **otwarcie okna dialogowego Dodawanie** nowego projektu z wybranym projektem Kreatora **wdrażania** zdalnego.

  Kreator wdrażania zdalnego prosi o podanie typu aplikacji (systemu Windows lub sieci Web), grup danych wyjściowych projektu do dołączyć, wszelkich dodatkowych plików, które mają zostać dołączyć, oraz komputera zdalnego, na którym chcesz wdrożyć. Ostatnia strona kreatora zawiera podsumowanie wybranych opcji.

  Projekty, które są przedmiotem procesu wdrażania, dają elementy wyjściowe, które muszą zostać przeniesione do środowiska alternatywnego. Te elementy wyjściowe są opisane jako parametry interfejsu, którego głównym celem jest umożliwienie projektom <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> grupowania danych wyjściowych. Aby uzyskać więcej informacji dotyczących implementacji `IVsProjectCfg2` programu , zobacz Project Configuration for Output [(Konfiguracja projektu dla danych wyjściowych).](../../extensibility/internals/project-configuration-for-output.md)

  Projekty wdrażania, które zarządzają procesem wdrażania, włącz polecenie Deploy i odpowiedz po wybraniu tego polecenia. Projekty wdrażania implementują interfejs do wykonywania wdrożenia i wykonywania wywołań do <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interfejsu w celu zgłaszania zdarzeń stanu wdrażania.

  Konfiguracje mogą określać zależności, które mają wpływ na ich operacje kompilacji lub wdrażania. Zależności kompilacji lub wdrażania to projekty, które muszą zostać skompilowane lub wdrożone przed lub po skompilowaniu lub wdrożeniu samych konfiguracji. Zależności kompilacji między projektami są opisane za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interfejsu i wdrażane za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfejsu. Aby uzyskać więcej informacji, zobacz [Project Configuration for Building](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
