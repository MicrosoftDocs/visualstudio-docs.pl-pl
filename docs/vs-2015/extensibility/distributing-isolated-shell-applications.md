---
title: Dystrybuowanie aplikacji Isolated Shell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27228131c1e955a394e666ac05f0ddd68c879be0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758778"
---
# <a name="distributing-isolated-shell-applications"></a>Dystrybuowanie aplikacji Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby można było utworzyć aplikacji isolated shell, należy zainstalować program Visual Studio i zestawu SDK programu Visual Studio. Dystrybucji aplikacji na komputerach innych użytkowników oraz klientów, musi zawierać specjalnych pakietu redystrybucyjnego dla programu isolated shell.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Wymagania wstępne dotyczące dystrybuowanie aplikacji Isolated Shell  
  
|Nazwa|Opis|  
|----------|-----------------|  
|Visual Studio SDK|Zestaw SDK, konieczne jest posiadanie na opracowywanie i testowanie rozszerzenia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Zestaw SDK umożliwia również tworzenie własnego wystąpienia powłoki programu Visual Studio, izolowany.<br /><br /> Program Visual Studio jest wymaganiem wstępnym dla zestawu SDK.|  
|Microsoft Visual Studio Isolated Shell do dystrybucji|Pakiet redystrybucyjny programu objęte program instalacyjny, podczas tworzenia środowiska narzędzi programu Visual Studio isolated shell. Pakiet redystrybucyjny isolated Shell obejmuje .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Tworzenie programu instalacyjnego dla aplikacji  
 Program specjalnej instalacji należy utworzyć dla powłoki lub odizolowane w zintegrowanej aplikacji. Aby uzyskać więcej informacji, zobacz [instalowania aplikacji izolowanej powłoki](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Zezwalanie na aktualizacje aplikacji  
 Program instalacyjny musi zezwalać na możliwość, że aplikacji zostaną zaktualizowane, za pomocą funkcji Aktualizacje firmy Microsoft lub za pomocą funkcji Aktualizacje w firmie. Aby uzyskać więcej informacji o aktualizacjach, zobacz [obsługi wytyczne dotyczące aplikacje izolowane powłoki](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).

