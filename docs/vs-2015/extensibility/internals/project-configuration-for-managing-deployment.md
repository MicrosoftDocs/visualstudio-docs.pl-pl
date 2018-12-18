---
title: Projekt konfiguracji do zarządzania wdrożeniem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6ea732449c92b2dffb91c7e90ff738791b7c2f7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721362"
---
# <a name="project-configuration-for-managing-deployment"></a>Konfigurowanie projektu do zarządzania wdrożeniem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wdrożenie jest fizycznie przeniesienie elementów wyjściowych z procesu kompilacji w oczekiwanej lokalizacji debugowania i podczas instalacji. Na przykład aplikacja sieci Web może być oparta na komputerze lokalnym i następnie umieszczone na serwerze.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługuje dwie metody, które projekty mogą brać udział we wdrożeniu:  
  
- Jako podmiot w procesie wdrażania.  
  
- Jako Menedżer ds. procesu wdrażania.  
  
  Przed wdrożeniem rozwiązania, należy najpierw dodać projekt wdrożenia, aby skonfigurować opcje wdrażania. Jeśli projekt Wdróż jeszcze nie istnieje, zostanie wyświetlony monit Jeśli chcesz utworzyć po wybraniu **wdrożyć rozwiązanie** z **kompilacji** menu lub kliknij prawym przyciskiem myszy rozwiązanie. Klikając **tak** otwiera **Dodaj nowy projekt** okno dialogowe z **Kreator zdalnego wdrażania** wybranego projektu.  
  
  Kreator zdalnego wdrażania pyta dla typu aplikacji (Windows lub w sieci Web), grupy danych wyjściowych projektu do uwzględnienia, wszelkie dodatkowe pliki, które mają zostać uwzględnione i komputer zdalny, którą chcesz wdrożyć. Ostatnia strona kreatora Wyświetla podsumowanie wybrane opcje.  
  
  Projekty, które są objęte procesem wdrażania generuje elementy danych wyjściowych, które należy przenieść do środowiska alternatywne. Te dane wyjściowe elementy są określane jako parametry <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interfejsu, którego podstawowy cel if umożliwić projekty do grupy danych wyjściowych. Aby uzyskać więcej informacji dotyczących implementacji `IVsProjectCfg2`, zobacz [konfiguracji projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).  
  
  Projekty wdrażania, których zarządzanie procesem wdrażania, włącz polecenie wdrożenia i reagować po wybraniu tego polecenia. Projekty wdrażania w implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfejsu, aby wykonać wdrożenie i wykonywać wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interfejsu do raportu wdrażania stan zdarzenia.  
  
  Konfiguracje można określić zależności, które mają wpływ na operacje kompilacji lub wdrożenia. Kompilowania lub wdrażania zależności są projektami, które muszą być skompilowane lub wdrożone przed lub po same konfiguracje są kompilowania lub wdrażania. Opisano zależności kompilacji między projektami za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interfejs i wdrożenie zależności za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfejsu. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)   
 [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)

