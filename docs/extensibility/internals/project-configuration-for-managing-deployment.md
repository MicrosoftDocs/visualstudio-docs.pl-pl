---
title: Konfiguracja projektu do zarządzania wdrażaniem | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62f7bf6535a89e46799ade88fe8976974b3019c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706709"
---
# <a name="project-configuration-for-managing-deployment"></a>Konfigurowanie projektu do zarządzania wdrożeniem
Wdrożenie jest aktem fizycznego przenoszenia elementów wyjściowych z procesu kompilacji do oczekiwanej lokalizacji do debugowania i instalacji. Na przykład aplikacja sieci Web może być zbudowana na komputerze lokalnym, a następnie umieszczona na serwerze.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]obsługuje dwa sposoby zaangażowania projektów we wdrażanie:

- Jako temat procesu wdrażania.

- Jako menedżer procesu wdrażania.

  Przed wdrożeniem rozwiązań należy najpierw dodać projekt wdrożenia, aby skonfigurować opcje wdrażania. Jeśli projekt wdrażania jeszcze nie istnieje, zostanie wyświetlony monit, czy chcesz go utworzyć po **wybraniu opcji Wdrażanie rozwiązania** z menu **Kompilacja** lub kliknięciu prawym przyciskiem myszy rozwiązania. Kliknięcie **przycisku Tak** powoduje otwarcie okna dialogowego **Dodawanie nowego projektu** z zaznaczonym projektem **Kreatora wdrażania zdalnego.**

  Kreator wdrażania zdalnego prosi o uwzględnienie typu aplikacji (Windows lub Web), grup wyjściowych projektu, wszelkich dodatkowych plików, które chcesz dołączyć, oraz komputera zdalnego, na który chcesz wdrożyć. Na ostatniej stronie kreatora jest wyświetlane podsumowanie wybranych opcji.

  Projekty, które są przedmiotem procesu wdrażania produkcji elementów wyjściowych, które muszą zostać przeniesione do środowiska alternatywnego. Te elementy wyjściowe są opisane <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> jako parametry interfejsu, którego głównym celem, jeśli zezwolić projektom na grupowanie wyników. Aby uzyskać więcej informacji dotyczących `IVsProjectCfg2`implementacji programu , zobacz [Konfiguracja projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).

  Projekty wdrażania, które zarządzają procesem wdrażania, włączyć polecenie Deploy i reagować po wybraniu tego polecenia. Projekty wdrażania <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> implementują interfejs do wykonywania wdrażania <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> i nawiązywać połączenia z interfejsem, aby zgłosić zdarzenia stanu wdrażania.

  Konfiguracje można określić zależności, które wpływają na ich operacji kompilacji lub wdrażania. Build lub deploy zależności są projekty, które muszą być utworzone lub wdrożone przed lub po konfiguracje same są budowane lub wdrażane. Zależności kompilacji między projektami <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> są opisane za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfejsu i wdrożyć zależności z interfejsem. Aby uzyskać więcej informacji, zobacz [Konfiguracja projektu dla tworzenia](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
