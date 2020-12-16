---
title: 'Instrukcje: kierowanie wielojęzycznego interfejsu użytkownika pakietu Office'
description: Dowiedz się, jak można użyć programu Visual Studio do programistycznego ukierunkowania Microsoft Office wielojęzycznego interfejsu użytkownika.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6b6771b202515148b757e811fdfc63fc0d5052e9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526629"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Instrukcje: kierowanie wielojęzycznego interfejsu użytkownika pakietu Office
  Wielojęzycznego interfejsu użytkownika (MUI) to Microsoft Office funkcja, która daje użytkownikowi końcowemu możliwość zmiany języka interfejsu użytkownika. Na przykład użytkownik końcowy pracujący z angielskim interfejsem użytkownika może zmienić język interfejsu użytkownika na hiszpański.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Jeśli aplikacja będzie używana przez osoby korzystające z wielu języków pakietu Office, można dodać kod w celu automatycznego zmiany języka ciągów interfejsu użytkownika w celu dopasowania go do języka używanego przez pakiet Office na komputerze użytkownika (Jeśli użytkownik ma zainstalowane poprawne zasoby).

## <a name="to-check-the-current-office-ui-setting"></a>Aby sprawdzić bieżące ustawienie interfejsu użytkownika pakietu Office

1. Użyj <xref:System.Threading.Thread.CurrentUICulture%2A> właściwości bieżącego wątku. Ustaw język ciągów interfejsu użytkownika tak, aby był zgodny z językiem używanym przez wersję pakietu Office, która jest aktualnie uruchomiona na komputerze użytkownika.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>Zobacz też
- [Jak: docelowa aplikacja pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)
