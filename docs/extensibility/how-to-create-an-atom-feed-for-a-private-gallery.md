---
title: 'Jak: Tworzenie kanału informacyjnego Atom dla galerii prywatnej | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72fbf2d3973ffd84de1cf6f33788c43511c3ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711013"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Jak: Tworzenie kanału informacyjnego Atom dla prywatnej galerii
Kanał informacyjny Atom (RSS) można utworzyć w lokalizacji intranetowej zawierającej rozszerzenia i dodać go do **rozszerzenia i aktualizacji** jako galerię prywatną. Aby uzyskać więcej informacji, zobacz [Prywatne galerie](../extensibility/private-galleries.md).

## <a name="create-an-atom-feed"></a>Tworzenie kanału atomowego
 Aby utworzyć kanał Atom jako prywatną galerię, należy najpierw zebrać rozszerzenia (pliki*vsix)* do folderu. Jeśli chcesz, możesz je uporządkować w podfoldery. Potrzebne będą również następujące zasoby:

- Plik *atom.xml,* który udostępnia rozszerzenia jako galerię prywatną. Aby uzyskać informacje dotyczące podłączania pliku *atom.xml* do **rozszerzeń i aktualizacji**, zobacz [Prywatne galerie](../extensibility/private-galleries.md).

- Folder zawierający wszystkie pliki obrazów wyodrębnione z rozszerzeń (na przykład zrzuty ekranu). Plik *atom.xml* zawiera względne łącza do tych obrazów, dzięki czemu są one dostępne w **rozszerzeniach i aktualizacjach**.

  Załóżmy na przykład, że zebrałeś następujące dwa rozszerzenia do folderu:

- *Template_Wizard_239.vsix*, który jest pustym szablonem projektu VSIX.

- *SelectionHighlight.vsix*, który jest narzędziem do podświetlania wszystkich wystąpień wybranego wyrazu.

  Zawartość pliku *atom.xml* będzie przypominać następujący przykład:

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

 Należy zauważyć, że dwa znaczniki linków odnoszą się do zrzutów ekranu w wygenerowanym folderze obrazów.

## <a name="see-also"></a>Zobacz też
- [Prywatne galerie](../extensibility/private-galleries.md)
