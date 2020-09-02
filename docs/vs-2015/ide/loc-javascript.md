---
title: '&lt;Loc &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf6016b2c12fd5ebe7cfb76c14c776508d99d2db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651476"
---
# <a name="ltlocgt-javascript"></a>&lt;Loc &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa lokalizację i typ pliku przyczepki, który zawiera zlokalizowane informacje IntelliSense.

## <a name="syntax"></a>Składnia

```
<loc filename="filename"
    format="vsdoc|messagebundle" />
```

#### <a name="parameters"></a>Parametry
 `filename` Obowiązkowe. Nazwa główna pliku przyczepki, który zawiera informacje o lokalizacji dla kultury neutralnej. Gdy program Visual Studio wyszukuje informacje o lokalizacji, próbuje znaleźć wersję tego pliku specyficzną dla kultury. Na przykład jeśli `filename` jquery.xml, Visual Studio szuka poprawnego folderu specyficznego dla kultury (jak ja) w tej samej lokalizacji, w której znajduje się plik. js, który zawiera `<loc>` element. Jeśli zlokalizuje folder specyficzny dla kultury, sprawdza, czy plik jquery.xml istnieje w nim. Jeśli nie można znaleźć poprawnego pliku, zamiast tego używa reguł lokalizacji zarządzanych zasobów. Wartość domyślna w polu `filename` to nazwa bieżącego pliku, ale z rozszerzeniem. xml zamiast. js.

 `format` Obowiązkowe. Typ pliku przyczepki używany do lokalizacji. Użyj `messagebundle` , aby określić użycie pakietów komunikatów zdefiniowanych przez otwarte metadane AJAX. `messagebundle` jest to zalecany format. Jednak ten format nie jest obsługiwany w programie Microsoft Ajax ani w plikach WinMD. Służy `vsdoc` do określania standardowego formatu lokalizacji .NET Framework, który jest używany przez Microsoft Ajax i środowisko wykonawcze systemu Windows. Ten atrybut jest opcjonalny. `vsdoc` jest formatem domyślnym.

## <a name="remarks"></a>Uwagi
 `<loc>`Element musi pojawić się u góry pliku w tej samej sekcji co `<reference>` element. Reguły użycia dla `<loc>` elementu są takie same jak dla `<reference>` elementu. Aby uzyskać więcej informacji, zobacz sekcję "dyrektywy referencyjne" w [JavaScript IntelliSense](../ide/javascript-intellisense.md).

 Program Visual Studio przetwarza pojedynczy `<loc>` element dla każdego pliku. js. W przypadku `<loc>` obecności wielu elementów używany jest tylko jeden `<loc>` element. Zachowanie podczas określania, którego `<loc>` elementu użyć nie jest zdefiniowane.

 W przypadku korzystania z formatu pakietu komunikatów należy użyć `locid` atrybutu w komentarzach dokumentacji XML, aby określić `name` wartość atrybutu.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak używać `<loc>` elementu z formatem MessageBundle. Dodaj następujący kod XML do pliku o nazwie messageFilename.xml i umieść go w poprawnym folderze specyficznym dla kultury, jak określono w opisie `filename` parametru.

```
<?xml version="1.0" encoding="utf-8" ?>
<messagebundle>
  <msg name="1">A class that represents a rectangle</msg>
  <msg name="2">The height of a rectangle</msg>
  <msg name="3">The width of a rectangle</msg>
</messagebundle>

```

 Aby uzyskać przykład messagebundle, Dodaj następujący kod do pliku JavaScript w projekcie. `<loc>`Element musi być wyświetlany jako pierwszy wiersz w pliku JavaScript. Opisy w tym kodzie zostaną zastąpione przez zlokalizowane opisy, jeśli są dostępne.

```javascript
/// <loc filename="messageFilename.xml" format="messagebundle"/>

function doSomething(a,b)
{
    /// <summary locid='1'>description</summary>
    /// <param name='a' locid='2'>parameter a description</param>
    /// <param name='b' locid='3'>parameter b description</param>
}

```

 W poniższym przykładzie zastosowano format VSDoc. Dodaj następujący kod XML do pliku o nazwie scriptFilename.xml i umieść go w prawidłowym folderze specyficznym dla kultury.

```
<?xml version="1.0" encoding="utf-8" ?>
<doc>
  <assembly>
    <name>Lights</name>
  </assembly>
  <members>
    <member name="M:illuminate">
      <summary>Activates a light. </summary>
      <param name='a'>The light to activate. </param>
    </member>
  </members>
</doc>

```

 Aby uzyskać przykład VSDoc, Dodaj następujący kod do pliku JavaScript w projekcie. Opisy w tym kodzie zostaną zastąpione przez zlokalizowane opisy, jeśli są dostępne.

```javascript
/// <loc filename="scriptFilename.xml" format="vsdoc" />

function illuminate(a)
{
    /// <summary locid='M:illuminate'>description</summary>
    /// <param name='a' type='Number'>parameter a description</param>
}

```

## <a name="see-also"></a>Zobacz też
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
