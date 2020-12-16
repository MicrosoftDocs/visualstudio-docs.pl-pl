---
title: 'Instrukcje: programowe pobieranie folderu według nazwy'
description: Dowiedz się, jak można użyć programu Visual Studio, aby programowo pobrać folder według nazwy, a następnie wyświetlić zawartość folderu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: c4e615897fedcbfa41ad7958e93354718d9ccfbc
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528569"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>Instrukcje: programowe pobieranie folderu według nazwy
  Ten przykład pobiera odwołanie do nazwanego folderu niestandardowego, a następnie wyświetla zawartość folderu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga:

- Folder o nazwie TestFolder.

## <a name="see-also"></a>Zobacz też
- [Pracuj z folderami](../vsto/working-with-folders.md)
- [Instrukcje: programowe wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Instrukcje: programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Instrukcje: Programowane tworzenie niestandardowych elementów folderów](../vsto/how-to-programmatically-create-custom-folder-items.md)
