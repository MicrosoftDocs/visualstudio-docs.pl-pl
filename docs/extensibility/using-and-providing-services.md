---
title: Korzystanie z usług i świadczenie usług | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8741d8d66af96ad4c6abea44b238393a34c5aa95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698742"
---
# <a name="using-and-providing-services"></a>Korzystanie z usług i dostarczanie ich
Usługa jest umową między dwoma vspackages. Jeden VSPackage oferuje określony zestaw interfejsów dla innego VSPackage do wykorzystania. Na przykład [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oferuje <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> usługę do dowolnego VSPackage ładuje. Ta usługa <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> udostępnia interfejs, który może służyć do zapisu w dzienniku aktywności. Aby uzyskać więcej informacji, zobacz [Jak: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).

 Pakiety VSPackages można oferować własne <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> usługi przy użyciu interfejsu..

 Visual Studio oferuje ważne usługi, takie jak następujące:

|Usługa IDE|Opis|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Zapewnia dostęp do usług IDE zajmujących się podstawowymi funkcjami, pakietami VSPackage i rejestrem.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Zapewnia podstawowe okna i funkcje związane z interfejsem użytkownika w IDE, takie jak możliwość tworzenia narzędzi i okien dokumentów.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Zapewnia podstawowe funkcje związane z rozwiązaniami, takie jak możliwość wyliczanie projektów, tworzenie nowych projektów i monitorowanie zmian projektu.|

## <a name="in-this-section"></a>W tej sekcji
- [Podstawowe usługi](../extensibility/internals/service-essentials.md) Przedstawia ważne elementy usługi Visual Studio.

- [Jak: Uzyskaj usługę](../extensibility/how-to-get-a-service.md) W tym artykule omówiono sposób żądania (zużywają) usługi.

- [Jak: Świadczenie usług](../extensibility/how-to-provide-a-service.md) W tym artykule omówiono sposób świadczenia usługi.

- [Jak: Zapewnienie usługi Asynchronous Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) W tym artykule omówiono sposób świadczenia usługi asynchroniiowej.

- [Jak: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md) Omawia typowe problemy i przedstawia rozwiązania dla nich.

## <a name="related-sections"></a>Sekcje pokrewne
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
