---
title: Korzystanie z usług i dostarczanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c9b0dbf2122b5a76d557cdd70da27660b886041
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337038"
---
# <a name="using-and-providing-services"></a>Korzystanie z usług i dostarczanie ich
Usługa jest Umowa między dwoma pakietami VSPackage. Jednego pakietu VSPackage oferuje zestaw określonych interfejsów dla innego pakietu VSPackage korzystać. Na przykład [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oferuje <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> do dowolnego pakietu VSPackage go obsłużyć obciążenia. Ta usługa zapewnia <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejs, który może służyć do zapisu w dzienniku aktywności. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).

 Pakietów VSPackage może oferować swoje własne przy użyciu usług <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfejs...

 Program Visual Studio udostępnia ważne usługi, takie jak następujące:

|Usługa środowiska IDE|Opis|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Zapewnia dostęp do środowiska IDE usług radzenia sobie z podstawowych funkcji, pakietów VSPackage i rejestru.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Udostępnia podstawowe obsługi okien i związane z interfejsem użytkownika w środowisku IDE, takie jak możliwość tworzenia, narzędzi i oknami dokumentu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Zapewnia podstawowe funkcje związane z rozwiązania, takimi jak wyliczyć projektów, Utwórz nowe projekty i monitorowanie zmian projektu.|

## <a name="in-this-section"></a>W tej sekcji
- [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md) przedstawiono ważne elementy usługi Visual Studio.

- [Instrukcje: Usługi](../extensibility/how-to-get-a-service.md) w tym artykule omówiono sposób żądania (Używanie) usługi.

- [Instrukcje: Oferuje usługi](../extensibility/how-to-provide-a-service.md) w tym artykule omówiono sposób zapewniania usług.

- [Instrukcje: Podaj asynchroniczne usługi Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) w tym artykule omówiono sposób obsługi asynchronicznej.

- [Instrukcje: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md) w tym artykule omówiono typowe problemy i przedstawia informacje o rozwiązaniach do nich.

## <a name="related-sections"></a>Sekcje pokrewne
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)