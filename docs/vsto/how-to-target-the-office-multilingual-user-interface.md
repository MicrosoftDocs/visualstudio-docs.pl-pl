---
title: 'Instrukcje: Docelowy urząd wielojęzyczny interfejs użytkownika'
ms.date: 02/02/2017
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e911563406e0cfdeff613f70a5059da34c4b66df
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872284"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Instrukcje: Docelowy urząd wielojęzyczny interfejs użytkownika
  Wielojęzyczny interfejs użytkownika (MUI) to funkcja pakietu Microsoft Office, który umożliwia użytkownikowi końcowemu zmianę języka interfejsu użytkownika (UI). Na przykład użytkownik końcowy pracy przy użyciu interfejsu użytkownika w języku angielskim zmienić język interfejsu użytkownika na hiszpański.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Jeśli aplikacja będzie używane przez osoby korzystające z wielu języków, pakietu Office, możesz dodać kod, aby automatycznie zmienić język Twojej ciągi interfejsu użytkownika, język używany przez pakiet Office na komputerze użytkownika (Jeśli użytkownik ma prawidłowe zasoby zainstalowane).  
  
## <a name="to-check-the-current-office-ui-setting"></a>Aby sprawdzić bieżące ustawienia interfejsu użytkownika pakietu Office  
  
1.  Użyj <xref:System.Threading.Thread.CurrentUICulture%2A> właściwości bieżącego wątku. Ustawić język Twojej ciągi interfejsu użytkownika, język używany przez wersję pakietu Office, który działa obecnie na komputerze użytkownika.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)  
