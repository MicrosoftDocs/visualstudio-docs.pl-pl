---
title: 'Instrukcje: Utwórz Atom dla galerii prywatnej | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094bff5c761a45e936f14f79587b4846d3838610
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722411"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Instrukcje: Tworzenie źródła danych dla galerii prywatnej Atom
Można utworzyć kanału Atom (RSS) do lokalizacji intranetowej, która nie zawiera rozszerzenia i Dodaj źródło danych do **rozszerzenia i aktualizacje** jako prywatną galerię. Aby uzyskać więcej informacji, zobacz [galerie prywatne](../extensibility/private-galleries.md).

## <a name="create-an-atom-feed"></a>Tworzenie źródła danych Atom
 Aby utworzyć źródła danych jako prywatną galerię Atom, najpierw Zbierz rozszerzeń (*.vsix* plików) do folderu. Możesz organizować je w podfolderach chcącym. Należy również następujące zasoby:

- *Atom.xml* pliku, który udostępnia rozszerzenia jako prywatną galerię. Aby uzyskać informacje o tym, jak połączyć *atom.xml* plik **rozszerzenia i aktualizacje**, zobacz [galerie prywatne](../extensibility/private-galleries.md).

- Folder, który zawiera pliki obrazów, które zostały wyodrębnione ze rozszerzenia (na przykład zrzuty ekranu). *Atom.xml* plik zawiera linków względnych do tych obrazów, tak aby były dostępne w **rozszerzenia i aktualizacje**.

  Na przykład załóżmy, że zostały zebrane następujące dwa rozszerzenia do folderu:

- *Template_Wizard_239.vsix*, który jest pusty szablon projektu VSIX.

- *SelectionHighlight.vsix*, czyli narzędzie, aby wyróżnić wszystkie wystąpienia wybranego programu word.

  Zawartość *atom.xml* plik będzie wyglądać następująco:

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

 Należy zauważyć, że tagów łącza dwóch odnoszą się do zrzutów ekranu w folderze wygenerowanych obrazów.

## <a name="see-also"></a>Zobacz także
- [Galerie prywatne](../extensibility/private-galleries.md)
