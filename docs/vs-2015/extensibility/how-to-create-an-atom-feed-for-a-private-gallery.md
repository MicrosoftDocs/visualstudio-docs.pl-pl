---
title: 'Instrukcje: Utwórz Atom dla galerii prywatnej | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6d4ba78028774e8fbf8e281afa2855781dab43a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204211"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Instrukcje: Tworzenie strumieniowego źródła Atom dla galerii prywatnej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można utworzyć kanału Atom (RSS) do lokalizacji intranetowej, która nie zawiera rozszerzenia i Dodaj źródło danych do **rozszerzenia i aktualizacje** jako prywatną galerię. Aby uzyskać więcej informacji, zobacz [galerie prywatne](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Tworzenie Atom kanału informacyjnego  
 Aby utworzyć źródła danych jako prywatną galerię Atom, najpierw Zbierz do folderu rozszerzeń (plików .vsix). Możesz organizować je w podfolderach chcącym. Należy również następujące zasoby:  
  
- Plik atom.xml, która udostępnia rozszerzenia jako prywatną galerię. Aby uzyskać informacje o tym, jak połączyć pliku atom.xml do **rozszerzenia i aktualizacje**, zobacz [galerie prywatne](../extensibility/private-galleries.md).  
  
- Folder, który zawiera pliki obrazów, które zostały wyodrębnione ze rozszerzenia (na przykład zrzuty ekranu). Plik atom.xml zawiera linków względnych do tych obrazów, tak aby były dostępne w **rozszerzenia i aktualizacje**.  
  
  Na przykład załóżmy, że zostały zebrane następujące dwa rozszerzenia do folderu:  
  
- Template_Wizard_239.vsix, który jest pusty szablon projektu VSIX.  
  
- SelectionHighlight.vsix, czyli narzędzie, aby wyróżnić wszystkie wystąpienia wybranego słowa.  
  
  Zawartość pliku atom.xml będzie wyglądać następująco:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ….</summary>   
  <published>2011-04-14T14:24:51-07:00</published>   
  <updated>2011-04-14T14:24:22-07:00</updated>   
- <author>  
  <name>Microsoft</name>   
  </author>  
  <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
  <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
  <content type="application/octet-stream" src="SelectionHighlight.vsix" />   
- <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
  <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
  <Version>1.31</Version>   
  <References />   
  <Rating xsi:nil="true" />   
  <RatingCount xsi:nil="true" />   
  <DownloadCount xsi:nil="true" />   
  </Vsix>  
  </entry>  
- <entry>  
  <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
  …  
  </entry>  
  </feed>  
  
```  
  
 Należy zauważyć, że tagów łącza dwóch odnoszą się do zrzutów ekranu w folderze wygenerowanych obrazów.  
  
## <a name="see-also"></a>Zobacz też  
 [Galerie prywatne](../extensibility/private-galleries.md)
