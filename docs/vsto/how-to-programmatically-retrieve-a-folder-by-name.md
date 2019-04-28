---
title: 'Instrukcje: Programowe pobieranie folderu według nazwy'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a494f954f3f670fb796b33a0dbd01e2512ad1d26
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955732"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>Instrukcje: Programowe pobieranie folderu według nazwy
  W tym przykładzie pobiera odwołanie do folderu o nazwie niestandardowego, a następnie wyświetla zawartość tego folderu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład wymaga:

- Folder o nazwie TestFolder.

## <a name="see-also"></a>Zobacz także
- [Praca z folderami](../vsto/working-with-folders.md)
- [Instrukcje: Programowe wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Instrukcje: Programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Instrukcje: Programowe tworzenie niestandardowych elementów folderu](../vsto/how-to-programmatically-create-custom-folder-items.md)
