---
title: 'How to: Target the Office multilingual user interface (Jak kierować do wielojęzycznego interfejsu użytkownika pakietu Office)'
description: Dowiedz się, jak za pomocą Visual Studio programowo kierować Microsoft Office wielojęzycznego interfejsu użytkownika.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3cf838b544ec78c8c7d6e9e2d6f1cb747e999ccd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823920"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>How to: Target the Office multilingual user interface (Jak kierować do wielojęzycznego interfejsu użytkownika pakietu Office)
  Interfejs wielojęzyczny interfejs użytkownika (MUI) to Microsoft Office, która umożliwia użytkownikowi końcowemu zmianę języka interfejsu użytkownika. Na przykład użytkownik końcowy pracujący z angielskim interfejsem użytkownika może zmienić język interfejsu użytkownika na hiszpański.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Jeśli aplikacja będzie używana przez osoby korzystające z wielu języków pakietu Office, możesz dodać kod, aby automatycznie zmienić język ciągów interfejsu użytkownika w celu dopasowania go do języka używanego przez pakiet Office na komputerze użytkownika (jeśli użytkownik ma zainstalowane odpowiednie zasoby).

## <a name="to-check-the-current-office-ui-setting"></a>Aby sprawdzić bieżące ustawienie interfejsu użytkownika pakietu Office

1. Użyj <xref:System.Threading.Thread.CurrentUICulture%2A> właściwości bieżącego wątku. Ustaw język ciągów interfejsu użytkownika na język używany przez wersję pakietu Office, która jest aktualnie uruchamiana na komputerze użytkownika.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="see-also"></a>Zobacz też
- [How to: Target Office applications through primary interop assemblies (Jak kierować aplikacje pakietu Office za pomocą podstawowych zestawów międzyoptykowych)](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Późne powiązanie w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)
