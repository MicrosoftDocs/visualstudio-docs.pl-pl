---
title: 'Instrukcje: programowe wyszukiwanie określonego kontaktu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d8b2302586fc09fcfec6420d97374197eae7e67
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547072"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>Instrukcje: programowe wyszukiwanie określonego kontaktu
  Ten przykład przeszukuje folder Kontakty programu Outlook pod kątem określonego kontaktu według imienia i nazwiska. W przykładzie przyjęto założenie, że kontakt o nazwie **Jan Evans** istnieje w folderze kontaktów.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z elementami kontaktów](../vsto/working-with-contact-items.md)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
