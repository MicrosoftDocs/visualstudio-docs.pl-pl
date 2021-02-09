---
title: Fragmenty kodu dla języka R
description: Fragmenty kodu dla języka R w programie Visual Studio udostępniają skróty umożliwiające szybkie Wstawianie bloków kodu o dowolnej długości, co pomaga uniknąć ponownego wpisywania podobnego kodu.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: ca2bc533f26843dcfc22eb1129a66020cd8a5a03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885810"
---
# <a name="code-snippets-for-r"></a>Fragmenty kodu dla języka R

Fragmenty kodu w programie Visual Studio udostępniają skróty umożliwiające szybkie Wstawianie bloków kodu o dowolnej długości, dzięki czemu można uniknąć ponownego wpisywania podobnego kodu. R Tools for Visual Studio (RTVS) dodaje dziesiątki przydatnych fragmentów kodu języka R do kolekcji programu Visual Studio.

Aby wstawić fragment kodu, wpisz skróconą nazwę fragmentu kodu (podano IntelliSense), a następnie naciśnij klawisz **Tab** , aby wstawić.

Niektóre proste przykłady:

- Wpisz `=` , a następnie Tab i RTVS rozszerza je do `<-` operatora przypisania.
- Wpisz, a `>` następnie Tab i RTVS rozszerza IT do `%>%` operatora potoku.

Fragmenty kodu mogą być znacznie dłuższe niż tylko znak uzupełniania znaków. Fragment kodu dotyczący odczytywania pliku CSV z `read.csv` funkcją, na przykład, może zwolnić użytkownika przed zapamiętaniem nazw lub parametrów:

![Animacja użycia fragmentu kodu w celu wstawienia wywołania do read.csv](media/code-snippet-expansion.gif)

W takim przypadku podczas wpisywania funkcja `readc` IntelliSense wyświetla listę uzupełniania. Zaznaczenie tego pola wyboru na liście rozwijanej i naciśnięcie klawisza **Tab** spowoduje zaznaczenie i `readc` naciśnięcie klawisza **Tab** ponownie rozszerza fragment kodu. (Z tego powodu rozwinięcie fragmentów jest często przemyślane jako "wpisz fragment kodu i naciśnij klawisz TAB dwa razy"). W większości przypadków pierwsza karta kończy wybór IntelliSense, a druga karta wyzwala rozszerzanie.

Aby wyświetlić wszystkie dostępne fragmenty kodu, Otwórz okno dialogowe   >  **Menedżer wstawek kodów** narzędzi (**Ctrl** + **K**,**B**) i wybierz pozycję **R** dla **języka**. Rozwiń grupy i wybierz poszczególne fragmenty kodu, aby wyświetlić opis i tekst skrótu:

![Okno dialogowe fragmenty kodu dla języka R](media/code-snippet-dialog.png)

Aby utworzyć niestandardowe fragmenty kodu, postępując zgodnie z instrukcjami w [przewodniku: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md). Ostatecznie fragment kodu jest tylko plikiem XML. Na przykład poniższy kod stanowi fragment dla operacji potoku (skrót `>` ):

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

Pliki XML dla wszystkich fragmentów kodu są instalowane z RTVS; w polu **Lokalizacja** w **Menedżerze fragmentów kodu** znajduje się ścieżka. Można je również znaleźć w kodzie źródłowym RTVS w serwisie GitHub w obszarze [src/Package/Impl/fragmenty](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets)kodu.
