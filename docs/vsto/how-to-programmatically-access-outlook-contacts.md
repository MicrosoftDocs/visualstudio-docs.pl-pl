---
title: 'Instrukcje: Programowy dostęp do kontaktów programu Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a9fc9cf214a8aebd663a7de29528790aa3cc0b46
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967686"
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

- Kontakty, w których ostatni nazwy zawierają ciąg "**Na"** (na przykład Tzipi Butnaru) w **kontakty** folderu.

## <a name="see-also"></a>Zobacz także
- [Praca z elementami kontaktów](../vsto/working-with-contact-items.md)
- [Instrukcje: Programowe Dodawanie wpisu do kontaktów programu Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Instrukcje: Programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Instrukcje: Programowe wyszukiwanie adresu e-mail w kontaktach](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Instrukcje: Programowe usuwanie kontaktów programu Outlook](../vsto/how-to-programmatically-delete-outlook-contacts.md)
