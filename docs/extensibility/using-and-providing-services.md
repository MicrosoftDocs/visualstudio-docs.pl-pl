---
title: Używanie i świadczenie usług | Microsoft Docs
description: Dowiedz się więcej na temat usług oferowanych przez środowisko IDE programu Visual Studio do pakietów VSPackage i używania. W tych artykułach opisano, jak uzyskać i udostępnić usługi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dbf04b5e4b032bc44040cf14f6bf23225696ee61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934128"
---
# <a name="using-and-providing-services"></a>Korzystanie z usług i dostarczanie ich
Usługa jest umową między dwoma pakietów VSPackage. Jeden pakietu VSPackage oferuje określony zestaw interfejsów dla innego pakietu VSPackage do użycia. Program udostępnia na przykład [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> usługę pakietu VSPackage. Ta usługa udostępnia <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejs, który może być używany do zapisywania w dzienniku aktywności. Aby uzyskać więcej informacji, zobacz [How to: Use the Activity Log](../extensibility/how-to-use-the-activity-log.md).

 Pakietów VSPackage mogą oferować własne usługi przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfejsu.

 Program Visual Studio oferuje ważne usługi, takie jak następujące:

|Usługa IDE|Opis|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Zapewnia dostęp do usług IDE związanych z podstawowymi funkcjami, pakietów VSPackage i rejestrem.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Zapewnia podstawowe funkcje związane z oknami i interfejsem użytkownika w IDE, takie jak możliwość tworzenia narzędzi i okien dokumentów.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Zawiera podstawowe funkcje związane z rozwiązaniami, takie jak możliwość wyliczania projektów, tworzenia nowych projektów i monitorowania zmian w projekcie.|

## <a name="in-this-section"></a>W tej sekcji
- [Podstawowa usługa](../extensibility/internals/service-essentials.md) Przedstawia ważne elementy usługi Visual Studio.

- [Instrukcje: Uzyskiwanie usługi](../extensibility/how-to-get-a-service.md) W tym artykule omówiono sposób żądania (użytkowania) usługi.

- [Instrukcje: dostarczanie usługi](../extensibility/how-to-provide-a-service.md) W tym artykule omówiono sposób świadczenia usługi.

- [Instrukcje: dostarczanie asynchronicznej usługi programu Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) W tym artykule omówiono sposób dostarczania usługi asynchronicznej.

- [Instrukcje: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md) Omawia typowe problemy i prezentuje do nich rozwiązania.

## <a name="related-sections"></a>Sekcje pokrewne
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
