---
title: Informacje o oknie rejestrów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4deaf03013b6e28ea02e6ec7412bd23a05f1b87e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72738249"
---
# <a name="about-the-registers-window-in-visual-studio-c-c-visual-basic-f"></a>Informacje o oknie rejestrów w programie Visual Studio (C#, C++, Visual Basic, F #)

Okno **rejestry** jest dostępne tylko wtedy, gdy w oknie dialogowym **Opcje** jest **włączone debugowanie na** poziomie adresu.

 Rejestry są specjalnymi lokalizacjami w ramach procesora (CPU), które są używane do przechowywania małych fragmentów danych, nad którymi pracuje procesor. Kompilowanie lub interpretowanie kodu źródłowego generuje instrukcje, które przenoszą dane z pamięci do rejestrów i ponownie z powrotem, zgodnie z wymaganiami. Uzyskiwanie dostępu do danych w rejestrach jest bardzo szybkie w porównaniu z dostępem do danych w pamięci, więc kod, który umożliwia procesorowi utrzymywanie danych w rejestrze i dostęp do nich wielokrotnie, jest wykonywany szybciej niż kod, który wymaga, aby procesor stale ładował i zwalnia rejestry. Aby ułatwić kompilatorowi przechowywanie danych w rejestrach i wykonywanie innych optymalizacji, należy unikać używania zmiennych globalnych i polegać na zmiennych lokalnych, jak to możliwe. Kod zapisany w ten sposób ma dobry charakter referencyjny. W niektórych językach, takich jak C/C++, programista może zadeklarować zmienną rejestru, która informuje kompilator, aby wypróbować zmienną w rejestrze przez cały czas. Aby uzyskać więcej informacji, zobacz [Rejestrowanie słowa kluczowego](https://msdn.microsoft.com/library/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).

 Rejestry mogą być podzielone na dwa typy: ogólnego przeznaczenia i specjalnego przeznaczenia. Rejestry ogólnego przeznaczenia przechowują dane na potrzeby operacji ogólnych, takich jak dodawanie dwóch liczb lub odwoływanie się do elementu w tablicy. Rejestry specjalnego przeznaczenia mają określone cele i wyspecjalizowane znaczenie. Dobrym przykładem jest rejestr wskaźników stosu, który jest używany przez procesor do śledzenia stosu wywołań programu. Jako programista prawdopodobnie nie będzie można bezpośrednio manipulować wskaźnikiem stosu. Niemniej jednak jest istotne dla prawidłowego funkcjonowania programu, ponieważ bez wskaźnika stosu, procesor nie wie, gdzie należy powrócić na końcu wywołania funkcji.

 Większość rejestrów ogólnego przeznaczenia przechowuje tylko jeden element danych. Na przykład pojedyncza liczba całkowita, liczba zmiennoprzecinkowa lub element tablicy. Niektóre nowsze procesory mają więcej rejestrów o nazwie rejestry wektorowe, które mogą przechowywać małą tablicę danych. Ponieważ przechowują tak dużo danych, rejestry wektorowe umożliwiają bardzo szybkie wykonywanie operacji dotyczących tablic. Rejestry wektorowe były najpierw używane na kosztownych, wysoko wydajnych komputerach, ale teraz stają się dostępne w mikroprocesorach, w których są używane do korzystania z intensywnych operacji graficznych.

 Procesor ma zazwyczaj dwa zestawy rejestrów ogólnego przeznaczenia, jeden zoptymalizowany dla operacji zmiennoprzecinkowych, a drugi dla operacji całkowitych. Nie Surprisingly, są one nazywane rejestrami zmiennoprzecinkowymi i liczbami całkowitymi.

 Kod zarządzany jest kompilowany w czasie wykonywania do kodu natywnego, który uzyskuje dostęp do rejestrów fizycznych mikroprocesora. W oknie **rejestry** są wyświetlane te rejestry fizyczne dla środowiska uruchomieniowego języka wspólnego lub kodu natywnego. W oknie **rejestrów** nie są wyświetlane informacje o rejestracji dla skryptu lub aplikacji SQL, ponieważ skrypty i SQL są językach, które nie obsługują koncepcji rejestrów.

 Aby uzyskać więcej informacji na temat wyświetlania okna **rejestrów** , zobacz [Korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md).

 Po przeszukaniu okna **rejestry** zobaczysz wpisy, takie jak `EAX = 003110D8` .

 Symbol po lewej stronie `=` znaku to nazwa rejestru, `EAX` w tym przypadku. Liczba z prawej strony `=` znaku reprezentuje zawartość rejestru.

 Okno **rejestry** pozwala robić więcej niż tylko wyświetlanie zawartości rejestru. Gdy jesteś w trybie przerwania w kodzie natywnym, możesz kliknąć zawartość rejestru i edytować wartość. Nie jest to coś, co należy robić losowo. Jeśli nie rozumiesz rejestru, który edytujesz, a zawarte w nim dane, wynik edycji nieostrożnej może być spowodowany awarią programu lub inną niepotrzebną konsekwencją. Niestety, szczegółowe wyjaśnienie zestawów rejestracji różnych procesorów Intel i Intel wykracza poza zakres tego krótkiego wprowadzenia.

## <a name="register-groups"></a>Rejestruj grupy

Aby zmniejszyć bałagan, okna **rejestry** organizują rejestry w grupy. Jeśli klikniesz prawym przyciskiem myszy okno **rejestry** , zobaczysz menu skrótów zawierające listę grup, które można wyświetlić lub ukryć, gdy zobaczysz dopasowanie.

## <a name="register-flags"></a>Zarejestruj flagi

W przypadku procesorów Intel x86 w oknie **rejestry** mogą pojawić się następujące flagi. Podczas sesji debugowania można także edytować te flagi.

|Flaga|Ustaw wartość|
|-|-|
|Przepływ|OV = 1|
|Kierunek|W GÓRĘ = 1|
|Zawieszenia|EI = 1|
|Znak|PL = 1|
|Zero|ZR = 1|
|Przeniesienie pomocnicze|AC = 1|
|Parity|PE = 1|
|Carry|CY = 1|

## <a name="see-also"></a>Zobacz też
- [Porady: korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)