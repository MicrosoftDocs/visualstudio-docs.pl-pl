---
title: Dystrybuowanie izolowanych aplikacji powłoki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204675"
---
# <a name="distributing-isolated-shell-applications"></a>Dystrybuowanie aplikacji w programie Shell (izolowanym)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby utworzyć izolowaną aplikację powłoki, należy zainstalować program Visual Studio i zestaw SDK programu Visual Studio. Aby przeprowadzić dystrybucję aplikacji do maszyn innych użytkowników lub klientów, należy dołączyć specjalny pakiet redystrybucyjny dla powłoki izolowanej.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Wymagania wstępne dotyczące dystrybucji izolowanych aplikacji powłoki  
  
|Nazwa|Opis|  
|----------|-----------------|  
|Visual Studio SDK|Zestaw SDK musi być konieczny do opracowania i przetestowania rozszerzeń [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Możesz również użyć zestawu SDK, aby utworzyć własne wystąpienie powłoki izolowanej programu Visual Studio.<br /><br /> Program Visual Studio jest wymaganiem wstępnym dla zestawu SDK.|  
|Microsoft Visual Studio redystrybucyjna izolowanej powłoki|Pakiet redystrybucyjny, który jest dołączany do programu instalacyjnego podczas tworzenia środowiska narzędzi w izolowanej powłoki programu Visual Studio. Pakiet redystrybucyjny izolowanej powłoki zawiera .NET Framework 4,5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Tworzenie programu instalacyjnego dla aplikacji  
 Należy utworzyć specjalny program instalacyjny dla aplikacji powłoki zintegrowanej lub izolowanej. Aby uzyskać więcej informacji, zobacz [Instalowanie izolowanej powłoki aplikacji](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Zezwalanie na aktualizacje aplikacji  
 Program instalacyjny musi zezwalać na możliwość aktualizowania aplikacji przez aktualizacje firmy Microsoft lub aktualizacje firmy. Aby uzyskać więcej informacji na temat aktualizacji, zobacz [wskazówki dotyczące obsługi dla izolowanych aplikacji powłoki](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
