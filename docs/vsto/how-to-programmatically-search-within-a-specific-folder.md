---
title: 'Instrukcje: Programowe wyszukiwanie w określonym folderze'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1427f0ab69cab2c23a0eeb7638bbc6e21778c55a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915497"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Instrukcje: Programowe wyszukiwanie w określonym folderze
  W tym przykładzie kodu użyto `Find` i `FindNext` metody, aby wyszukać tekst w polu tematu wiadomości e-mail, które znajdują się w **skrzynki odbiorczej**. Ta metoda używa filtru ciągów pod kątem litera T jako początkowa litera `Subject` tekstu.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z folderami](../vsto/working-with-folders.md)   
 [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)   
 [Instrukcje: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
