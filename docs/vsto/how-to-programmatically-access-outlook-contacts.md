---
title: 'Instrukcje: Programowy dostęp do kontaktów programu Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 662190d3db9c3d384d60f4953ea3809cb726f76c
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53801726"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Instrukcje: Programowy dostęp do kontaktów programu Outlook
  W tym przykładzie wyszukuje wszystkie kontakty, w których ostatni nazwy zawierają ciąg wyszukiwania.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Ten przykład wymaga:  
  
-   Kontakty, w których ostatni nazwy zawierają ciąg "**Na"** (na przykład Tzipi Butnaru) w **kontakty** folderu.  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z elementami kontaktów](../vsto/working-with-contact-items.md)   
 [Instrukcje: Programowe Dodawanie wpisu do kontaktów programu Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Instrukcje: Programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Instrukcje: Programowe wyszukiwanie adresu e-mail w kontaktach](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Instrukcje: Programowe usuwanie kontaktów programu Outlook](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  