---
title: '&lt;Lokalizacja&gt; (JavaScript) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8029dc6282e7b5a4ff9075257bcb1b6213a4a6b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758534"
---
# <a name="ltlocgt-javascript"></a>&lt;Lokalizacja&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa lokalizację i typ pliku sidecar, który zawiera zlokalizowane informacje funkcji IntelliSense.  
  
## <a name="syntax"></a>Składnia  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Opcjonalna. Nazwa głównego pliku sidecar, który zawiera informacje o lokalizacji dla kultury neutralnej. Gdy program Visual Studio wyszukuje informacji o lokalizacji, próbuje znaleźć wersji kulturowych tego pliku. Na przykład jeśli `filename` jest jquery.xml, Visual Studio wyszukuje poprawnego folderu specyficzne dla kultury (na przykład Japonia) w tej samej lokalizacji co plik .js, który zawiera `<loc>` elementu. Klient zlokalizuje folderu specyficzne dla kultury, sprawdza, czy istnieje plik jquery.xml w nim. Jeśli nie może odnaleźć prawidłowego pliku, zamiast tego używa zasady lokalizacji zasobów zarządzanych. Wartością domyślną dla `filename` jest nazwa bieżącego pliku, ale z rozszerzeniem .xml zamiast js.  
  
 `format`  
 Opcjonalna. Typ pliku sidecar używane dla lokalizacji. Użyj `messagebundle` Aby określić pakiety komunikat zdefiniowany przez metadane Otwórz Ajax. `messagebundle` jest to zalecany format. Jednak ten format nie jest obsługiwany w Microsoft Ajax lub pliki .winmd. Użyj `vsdoc` do określenia standardowym formacie lokalizacji środowiska .NET Framework, który jest używany przez Microsoft Ajax i środowiska wykonawczego Windows. Ten atrybut jest opcjonalny. `vsdoc` jest to format domyślny.  
  
## <a name="remarks"></a>Uwagi  
 `<loc>` Element musi znajdować się w górnej części pliku w tej samej sekcji, co `<reference>` elementu. Zasady użycia `<loc>` elementu są takie same jak `<reference>` elementu. Aby uzyskać więcej informacji, zobacz sekcję "Dyrektywy odwołania do" w [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
 Program Visual Studio przetwarza jeden `<loc>` elementu dla każdego pliku .js. Jeśli wiele `<loc>` istnieją elementy tylko jednego `<loc>` element jest używany. Zachowanie podczas określania, które `<loc>` nie zdefiniowano elementu do użycia.  
  
 Korzystając z formatu pakietu wiadomości, użyj `locid` atrybutu w komentarze dokumentacji XML, aby określić `name` wartość atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `<loc>` elementu przy użyciu formatu messagebundle. Dodaj następujący kod XML w pliku o nazwie messageFilename.xml i umieścić go w odpowiednim folderze specyficzne dla kultury, jak określono w opisie `filename` parametru.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 Na przykład messagebundle Dodaj następujący kod do pliku JavaScript w projekcie. `<loc>` Elementów musi występować jako pierwszy wiersz w pliku JavaScript. Opisy w tym kodzie zostanie zastąpiona przez opisy zlokalizowane, jeśli jest dostępny.  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 W poniższym przykładzie użyto VSDoc formatu. Dodaj następujący kod XML w pliku o nazwie scriptFilename.xml i umieścić go w odpowiednim folderze specyficzne dla kultury.  
  
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
  
 Na przykład VSDoc Dodaj następujący kod do pliku JavaScript w projekcie. Opisy w tym kodzie zostanie zastąpiona przez opisy zlokalizowane, jeśli jest dostępny.  
  
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
