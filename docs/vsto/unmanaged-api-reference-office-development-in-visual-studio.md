---
title: Niezarządzana dokumentacja interfejsu API (Programowanie Office w Visual Studio)
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 00db78359154dbda600fb4b58103bc04e89d16b2
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551324"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Niezarządzana dokumentacja interfejsu API (Programowanie Office w Visual Studio)

Począwszy od systemu 2007 Microsoft Office, aplikacje pakietu Office używają interfejsu [interfejsu IManagedAddin —](../vsto/imanagedaddin-interface.md) do wywołania składnika modułu ładującego narzędzi VSTO, który jest dołączony do programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Ten składnik służy do ułatwienia ładowania dodatków VSTO. Można utworzyć własny składnik modułu ładującego dodatku VSTO, implementując ten interfejs.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>W tej sekcji

[IManagedAddin —, interfejs](../vsto/imanagedaddin-interface.md)

Interfejs COM, który można zaimplementować w celu załadowania i zwolnienia zarządzanych dodatków narzędzi VSTO w aplikacjach pakietu Office.
