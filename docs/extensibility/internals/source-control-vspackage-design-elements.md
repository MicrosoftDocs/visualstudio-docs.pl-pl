---
title: Elementy projektu pakietu VSPackage kontroli źródła | Microsoft Docs
description: Dowiedz się więcej na temat struktury, którą pakietu VSPackage kontroli źródła musi zaimplementować, oraz interfejsów i usług, które może zaimplementować pakietu VSPackage kontroli źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e586470208989dce070c92963fc215f1053559a4
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877653"
---
# <a name="source-control-vspackage-design-elements"></a>Elementy projektu pakietu VSPackage kontroli kodu źródłowego
W tematach w tej sekcji przedstawiono strukturę, którą pakietu VSPackage kontroli źródła musi zaimplementować na potrzeby głębokiej integracji. Zawiera również listę interfejsów i usług, które pakietu VSPackage kontroli źródła może zaimplementować, oraz interfejsów i usług, których kontrola źródła pakietu VSPackage może użyć z innych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] składników do obsługi modelu i funkcjonalności kontroli źródła.

## <a name="in-this-section"></a>W tej sekcji
- [Struktura pakietu VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Definiuje strukturę pakietu VSPackage kontroli źródła.

- [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Wyświetla listę interfejsów i usług związanych z kontrolą źródła.

- [Dostępne usługi](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Opisuje usługę kontroli źródła zapewnioną przez pakietu VSPackage kontroli źródła.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)

 W tym artykule omówiono sposób tworzenia pakietu VSPackage kontroli źródła, które nie tylko dostarczają funkcji kontroli źródła, ale mogą służyć do dostosowywania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika kontroli źródła.
