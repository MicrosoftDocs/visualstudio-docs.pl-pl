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
ms.openlocfilehash: b9005b6cf7f23639481505a4727f8faa08241684
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433487"
---
# <a name="javascript-in-visual-studio"></a>Język JavaScript w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript jest językiem pierwszej klasy w programie Visual Studio. Podczas pisania kodu w języku JavaScript w środowisku IDE programu Visual Studio można używać większości lub wszystkich standardowych ułatwień edycji (fragmenty kodu, technologia IntelliSense itd.). W przypadku wielu typów aplikacji i usług, można napisać kod JavaScript.

 Aby uzyskać dokumentację referencyjną języka JavaScript, zobacz [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Określonych wersji programu Visual Studio lub określone rozszerzenia programu Visual Studio, może być konieczne opracowanie typów określonej aplikacji i usług przy użyciu języków HTML i JavaScript. Poniższa lista zawiera linki do dodatkowych informacji.

- Aby utworzyć aplikacje dla wielu platform przy użyciu Apache Cordova [pobieranie programu Visual Studio Tools for Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).

- Aby utworzyć [Windows Store](http://dev.windows.com/develop), [Windows Phone](http://dev.windows.com/develop)oraz aplikacje uniwersalne (obsługujących obu platform) [Pobierz narzędzia](https://developer.microsoft.com/windows/downloads).

- Aby utworzyć usług w chmurze, zobacz [witryny Microsoft Azure](http://azure.microsoft.com/documentation/).

- Do tworzenia witryn sieci web i aplikacji sieci web, [można znaleźć w witrynie ASP.NET](http://www.asp.net/get-started/websites).

  > [!NOTE]
  > Można tworzyć pusta witryna sieci Web platformy ASP.Net i użyć jej do programowania HTML, CSS i JavaScript. Plik Webconfig dostarczanego przez platformę ASP.NET, który powoduje włączenie debugowania w programie Visual Studio (lub po uruchomieniu aplikacji, można użyć narzędzia F12).

  Edytor kodu JavaScript w programie Visual Studio zapewnia obsługę technologii IntelliSense. Aby uzyskać więcej informacji, zobacz [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Co nowego w języku JavaScript
 W poniższej tabeli wymieniono nowe funkcje języka JavaScript.

|Funkcja|Opis|
|-------------|-----------------|
|Klasy|Nowa składnia obsługuje deklaracje [klasy](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class).|
|Obietnic|[Obietnic](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) umożliwia łatwiejsze i czyszcząca asynchronicznego programowania. Promise konstruktory są obsługiwane, wraz z `all` i `race` metody narzędziowe.|
|Iteratory|Teraz można wykonać iterację za pośrednictwem iterable obiektów (w tym tablice, tablicy obiektów i Iteratory), wywołując zaczepienia iteracji niestandardowych za pomocą instrukcji do wykonania dla wartości każdej różne właściwości. Aby uzyskać więcej informacji, zobacz [Iteratory i generatory kodu](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators). **Uwaga:**  Generatory nie są jeszcze obsługiwane.|
|Funkcje|W funkcji strzałkowej (= >) udostępnia skróconej składni `function` — słowo kluczowe, które funkcje leksykalne `this` powiązania.|
|Nowe metody dla wbudowanych obiektów|[Obiekt Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [Math — obiekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [numer obiektu](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [obiektu obiektu](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object), i [ciągu obiektu](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) wbudowane obiekty zawierają wiele nowych funkcji narzędzia i właściwości do manipulowania i inspekcji danych.|
|Ulepszenia literału obiektu|Obiekty obsługują obecnie obliczone właściwości, metody zwięzłe definicje i oczekiwaliśmy składni skrótu dla właściwości, której wartość jest inicjowany do zmiennej o tej samej nazwie. Aby uzyskać więcej informacji, zobacz [tworzenia obiektów](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Serwery proxy|[Serwery proxy](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) Włącz niestandardowe zachowanie dla obiektów.|
|Parametrów REST|Parametry REST umożliwiają włączenie następujących po sobie argumentów w wywołaniu funkcji do tablicy. Aby uzyskać więcej informacji, zobacz [funkcji](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Operator rozwijania|[Operator rozpiętości](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) (`…`) rozszerza iterable wyrażeń w oddzielne argumenty. Na przykład `a.b(…array)` jest w przybliżeniu taki sam jak `a.b.apply(a, array)`.|
|Symbole|[Symbol](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) obiektów Zezwalaj na właściwości, które mają zostać dodane do istniejących obiektów z możliwością nie zakłóceń z istniejącymi właściwościami obiektu, nie niezamierzone widoczności i innych dodatkach nieskoordynowane przez inny kod.|
|Ciągi szablonu|[Ciągi szablonu](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) są literały ciągu, które umożliwiają wyrażeń, które ma zostać obliczone i łączone za pomocą literału ciągu.|
|Ulepszenia Unicode|Wprowadzono ulepszenia do obsługi standardu Unicode. Na przykład nowy format sekwencji ucieczki obsługują punkty kodowe błyszczące (punkty kodowe z więcej niż cztery cyfry szesnastkowe). Aby uzyskać więcej informacji, zobacz [znaki specjalne](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|Weakset —|A [WeakSet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) to zbiór obiektów, które będą bezużyteczne, jeśli nie są przywoływane dowolnej innej lokalizacji.|
