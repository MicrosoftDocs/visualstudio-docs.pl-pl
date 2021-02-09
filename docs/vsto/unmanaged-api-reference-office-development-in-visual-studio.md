---
title: Niezarządzana dokumentacja interfejsu API (Programowanie Office w Visual Studio)
description: Niezarządzana dokumentacja interfejsu API jest używana w celu ułatwienia ładowania dodatków VSTO. Możesz również utworzyć własny składnik modułu ładującego dodatku VSTO, implementując ten interfejs.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cac9e2d01b47e0088543aeabcaeff30853314157
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908554"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Niezarządzana dokumentacja interfejsu API (Programowanie Office w Visual Studio)

Począwszy od systemu 2007 Microsoft Office, aplikacje pakietu Office używają interfejsu [interfejsu IManagedAddin —](../vsto/imanagedaddin-interface.md) do wywołania składnika modułu ładującego narzędzi VSTO, który jest dołączony do programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Ten składnik służy do ułatwienia ładowania dodatków VSTO. Można utworzyć własny składnik modułu ładującego dodatku VSTO, implementując ten interfejs.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>W tej sekcji

[IManagedAddin —, interfejs](../vsto/imanagedaddin-interface.md)

Interfejs COM, który można zaimplementować w celu załadowania i zwolnienia zarządzanych dodatków narzędzi VSTO w aplikacjach pakietu Office.
