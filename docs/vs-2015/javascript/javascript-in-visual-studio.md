---
title: JavaScript
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-javascript
ms.topic: conceptual
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 175cb6f6a8a3f240c244e139406841b0546209cc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295909"
---
# <a name="javascript-in-visual-studio"></a>Język JavaScript w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript jest językiem pierwszej klasy w programie Visual Studio. Podczas pisania kodu w języku JavaScript w środowisku IDE programu Visual Studio można używać większości lub wszystkich standardowych ułatwień edycji (fragmenty kodu, technologia IntelliSense itd.). W przypadku wielu typów aplikacji i usług, można napisać kod JavaScript.

 Aby uzyskać dokumentację referencyjną języka JavaScript, zobacz [JavaScript](https://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Określonych wersji programu Visual Studio lub określone rozszerzenia programu Visual Studio, może być konieczne opracowanie typów określonej aplikacji i usług przy użyciu języków HTML i JavaScript. Poniższa lista zawiera linki do dodatkowych informacji.

- Aby tworzyć aplikacje dla wielu platform przy użyciu Apache Cordova, [pobierz Visual Studio Tools dla Apache Cordova](https://go.microsoft.com/fwlink/p/?LinkId=397606).

- Aby utworzyć [Sklep Windows](https://developer.microsoft.com/), [Windows Phone](https://developer.microsoft.com/)i aplikacje uniwersalne (obsługujące obie platformy), [Pobierz narzędzia](https://developer.microsoft.com/windows/downloads).

- Aby utworzyć usługi oparte na chmurze, zobacz [witrynę Microsoft Azure](https://azure.microsoft.com/documentation/).

- Aby tworzyć witryny sieci Web i aplikacje sieci Web, [zobacz witrynę ASP.NET](https://dotnet.microsoft.com/apps/aspnet/web-apps).

  > [!NOTE]
  > Można tworzyć pusta witryna sieci Web platformy ASP.Net i użyć jej do programowania HTML, CSS i JavaScript. Plik Webconfig dostarczanego przez platformę ASP.NET, który powoduje włączenie debugowania w programie Visual Studio (lub po uruchomieniu aplikacji, można użyć narzędzia F12).

  Edytor kodu JavaScript w programie Visual Studio zapewnia obsługę technologii IntelliSense. Aby uzyskać więcej informacji, zobacz [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Co nowego w języku JavaScript
 W poniższej tabeli wymieniono nowe funkcje języka JavaScript.

|Funkcja|Opis|
|-------------|-----------------|
|Klasy|Nowa składnia obsługuje deklarację [klas](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class).|
|Obietnic|[Niesie obietnice zwiększenia](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) umożliwiają łatwiejsze i przejrzyste Kodowanie asynchroniczne. Obsługiwane są konstruktory Promise oraz metody narzędzi `all` i `race`.|
|Iteratory|Teraz można wykonać iterację za pośrednictwem iterable obiektów (w tym tablice, tablicy obiektów i Iteratory), wywołując zaczepienia iteracji niestandardowych za pomocą instrukcji do wykonania dla wartości każdej różne właściwości. Aby uzyskać więcej informacji, zobacz [Iteratory i generatory](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators). **Uwaga:**  Generatory nie są jeszcze obsługiwane.|
|Funkcje|Funkcja strzałka (= >) zawiera skróconą składnię słowa kluczowego `function`, która zawiera powiązanie `this` leksykalne.|
|Nowe metody dla wbudowanych obiektów|[Obiekt Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [obiekt matematyczny](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [obiekt Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [obiekt Object i](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)obiekty [typu String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) zawierają wiele nowych funkcji i właściwości narzędzi do manipulowania i inspekcji danych.|
|Ulepszenia literału obiektu|Obiekty obsługują obecnie obliczone właściwości, metody zwięzłe definicje i oczekiwaliśmy składni skrótu dla właściwości, której wartość jest inicjowany do zmiennej o tej samej nazwie. Aby uzyskać więcej informacji, zobacz [Tworzenie obiektów](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Serwery proxy|[Serwery proxy](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) umożliwiają zachowanie niestandardowe obiektów.|
|Parametrów REST|Parametry REST umożliwiają włączenie następujących po sobie argumentów w wywołaniu funkcji do tablicy. Aby uzyskać więcej informacji, zobacz [Functions](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Operator rozwijania|[Operator rozmieszczenia](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) (`…`) rozszerza wyrażenia iterowania na poszczególne argumenty. Na przykład `a.b(…array)` jest w przybliżeniu taka sama jak `a.b.apply(a, array)`.|
|Symbole|Obiekty [symboli](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) umożliwiają dodawanie właściwości do istniejących obiektów bez możliwości ingerencji z istniejącymi właściwościami obiektu, bez zamierzonej widoczności i bez innych nieskoordynowanych dodatków przez inny kod.|
|Ciągi szablonu|[Ciągi szablonów](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) są literałami ciągów, które umożliwiają ocenianie i łączenie wyrażeń z literałem ciągu.|
|Ulepszenia Unicode|Wprowadzono ulepszenia do obsługi standardu Unicode. Na przykład nowy format sekwencji ucieczki obsługują punkty kodowe błyszczące (punkty kodowe z więcej niż cztery cyfry szesnastkowe). Aby uzyskać więcej informacji, zobacz [znaki specjalne](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|Weakset —|[WeakSet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) to kolekcja obiektów, które będą zbierane jako elementy bezużyteczne, jeśli nie są one używane w innych miejscach.|
