---
title: 'Instrukcje: programowe uzyskiwanie dostępu do kontaktów programu Outlook'
description: Dowiedz się, jak można programistycznie uzyskiwać dostęp do kontaktów programu Outlook. Ten przykład umożliwia znalezienie wszystkich kontaktów, których nazwiska zawierają określony ciąg wyszukiwania.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7b82595aa3a09076b91211ba4ab45145b02ebcd9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903741"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Instrukcje: programowe uzyskiwanie dostępu do kontaktów programu Outlook
  Ten przykład umożliwia znalezienie wszystkich kontaktów, których nazwiska zawierają określony ciąg wyszukiwania.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga:

- Kontakty, których nazwiska zawierają ciąg "**na"** (na przykład Tzipi Butnaru) w folderze **kontaktów** .

## <a name="see-also"></a>Zobacz też
- [Pracuj z elementami kontaktów](../vsto/working-with-contact-items.md)
- [Instrukcje: programowe Dodawanie wpisu do kontaktów programu Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Instrukcje: programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Instrukcje: programowe wyszukiwanie adresu e-mail w kontaktach](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Instrukcje: programowe usuwanie kontaktów programu Outlook](../vsto/how-to-programmatically-delete-outlook-contacts.md)
