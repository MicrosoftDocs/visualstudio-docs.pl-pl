---
title: 'Instrukcje: tworzenie źródła danych Atom dla galerii prywatnej | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 269161e831fdb176dbfea844e951597efb467312
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905852"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Instrukcje: tworzenie kanału informacyjnego Atom dla galerii prywatnej
Można utworzyć źródło danych Atom (RSS) do lokalizacji intranetowej zawierającej rozszerzenia oraz dodać kanał informacyjny do **rozszerzeń i aktualizacji** jako galerii prywatnej. Aby uzyskać więcej informacji, zobacz [prywatne galerie](../extensibility/private-galleries.md).

## <a name="create-an-atom-feed"></a>Tworzenie źródła danych Atom
 Aby utworzyć źródło danych Atom jako galerię prywatną, należy najpierw zebrać rozszerzenia (pliki *. vsix* ) do folderu. Jeśli chcesz, możesz zorganizować je w podfolderach. Potrzebne będą również następujące zasoby:

- Plik *atom.xml* , który sprawia, że rozszerzenia są dostępne jako Galeria prywatna. Aby uzyskać informacje na temat sposobu łączenia pliku *atom.xml* z **rozszerzeniami i aktualizacjami**, zobacz [prywatne galerie](../extensibility/private-galleries.md).

- Folder, który zawiera wszystkie pliki obrazów wyodrębnione z rozszerzeń (na przykład zrzutów ekranu). Plik *atom.xml* zawiera linki względne do tych obrazów, dzięki czemu są one dostępne w **rozszerzeniach i aktualizacjach**.

  Załóżmy na przykład, że zebrano dwa następujące rozszerzenia w folderze:

- *Template_Wizard_239. vsix*, który jest pustym szablonem projektu VSIX.

- *SelectionHighlight. vsix*, który jest narzędziem do wyróżnienia wszystkich wystąpień zaznaczonego wyrazu.

  Zawartość pliku *atom.xml* będzie wyglądać następująco:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title type="text" />
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>
  <updated>2011-04-14T21:25:48Z</updated>
  <entry>
    <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>
    <title type="text">Highlight all occurrences of selected word</title>
    <summary type="text">This extends the editor to highlight ....</summary>
    <published>2011-04-14T14:24:51-07:00</published>
    <updated>2011-04-14T14:24:22-07:00</updated>
    <author>
      <name>Microsoft</name>
    </author>
    <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />
    <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />
    <content type="application/octet-stream" src="SelectionHighlight.vsix" />
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>
      <Version>1.31</Version>
      <References />
      <Rating xsi:nil="true" />
      <RatingCount xsi:nil="true" />
      <DownloadCount xsi:nil="true" />
    </Vsix>
  </entry>
  <entry>
    <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>
    ...
  </entry>
</feed>
```

 Zwróć uwagę, że dwa Tagi linków odnoszą się do zrzutów ekranu w wygenerowanym folderze obrazy.

## <a name="see-also"></a>Zobacz też
- [Galerie prywatne](../extensibility/private-galleries.md)
