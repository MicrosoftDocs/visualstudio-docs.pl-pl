---
title: 'Instrukcje: Programowe wyszukiwanie w określonym folderze'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5ac3dbb169fee82a55cc41b773d3616c56f83534
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638013"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Instrukcje: Programowe wyszukiwanie w określonym folderze
  W tym przykładzie kodu użyto `Find` i `FindNext` metody, aby wyszukać tekst w polu tematu wiadomości e-mail, które znajdują się w **skrzynki odbiorczej**. Ta metoda używa filtru ciągów pod kątem litera T jako początkowa litera `Subject` tekstu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Zobacz także
- [Praca z folderami](../vsto/working-with-folders.md)
- [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)
- [Instrukcje: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
