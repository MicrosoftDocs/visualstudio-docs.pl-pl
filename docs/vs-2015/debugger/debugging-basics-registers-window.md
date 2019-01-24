---
title: 'Podstawy debugowania: Okno rejestrów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3fc2ea04c79868fa515680f5c94eb3f600ee4884
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788656"
---
# <a name="debugging-basics-registers-window"></a>Podstawy debugowania: Okno rejestrów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Rejestruje** okno jest dostępne tylko wtedy, gdy debugowanie na poziomie adresów jest włączone w **opcje** okno dialogowe **debugowanie** węzła.  
  
 Rejestry są specjalne lokalizacje w ramach procesora (CPU), które są używane do przechowywania małych fragmentów danych, który procesor jest już aktywnie pracują nad. Kompilowanie lub interpretowanie kod źródłowy generuje instrukcje, które przenoszą dane z pamięci do rejestrów i z powrotem, zgodnie z potrzebami. Uzyskiwanie dostępu do danych w rejestrach jest bardzo szybkie uzyskiwanie dostępu do danych w pamięci, dzięki czemu kod, który umożliwia procesora do przechowywania danych w rejestrze, a następnie wielokrotnie do niego dostęp, zwykle działają szybciej niż kod, który wymaga procesora do stale ładowanie i zwalnianie rejestrów. Aby ułatwić kompilator, aby przechowywać dane w rejestrach i wykonywać inne optymalizacje, należy unikać używania zmiennych globalnych i zależą od zmiennych lokalnych, jak to możliwe. Kod napisany w ten sposób jest nazywany ma dobrą miejscowość odwołania. W przypadku niektórych języków, takich jak C/C++ programisty należy zadeklarować zmienną rejestru, który informuje kompilator, aby spróbować doskonale zapewnienie zmiennej w rejestrze przez cały czas. Aby uzyskać więcej informacji, zobacz [zarejestrować — słowo kluczowe](http://msdn.microsoft.com/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).  
  
 Rejestry można podzielić na dwa typy: ogólnego przeznaczenia i specjalnego przeznaczenia. Ogólnego przeznaczenia rejestrów przechowywania danych ogólne operacje, takie jak dodanie dwóch liczb lub odwołuje się do elementu w tablicy. Rejestruje specjalny ma określonych celów oraz specjalne znaczenie. Dobrym przykładem jest rejestrze wskaźnik stosu, który procesor jest używane do śledzenia stosu wywołań programu. Programistą będzie prawdopodobnie nie manipulować wskaźnik stosu bezpośrednio. Jest jednak niezbędne do prawidłowego funkcjonowania program ponieważ bez wskaźnik stosu procesora nie wiadomo, gdzie można powrócić do na końcu wywołania funkcji.  
  
 Większość rejestrów ogólnego przeznaczenia przechowują tylko danych jednego elementu. Na przykład pojedyncze liczby całkowite, liczba zmiennoprzecinkowa lub element tablicy. Niektóre procesory nowszej mają większe rejestrów, o nazwie rejestrów wektorowych, zawierających małą tablicę danych. Ponieważ przechowują tak dużej ilości danych, rejestrów wektorowych zezwala na operacje dotyczące tablic wykonywane bardzo szybko. Rejestrów wektorowych najpierw były używane na superkomputerów kosztownych, wysokiej wydajności, ale teraz stają się dostępne na mikroprocesorów, gdzie są one używane do wspaniałą korzyścią stosowania w ramach intensywnie korzystających z operacji graficznych.  
  
 Procesor ma zwykle dwa zestawy rejestrów ogólnego przeznaczenia, jeden zoptymalizowane pod kątem operacji zmiennoprzecinkowych i inne operacje liczby całkowitej. Nie zaskakująco są to tak zwane zmiennoprzecinkowe i rejestruje liczbę całkowitą.  
  
 Kod zarządzany jest kompilowana w czasie wykonywania do kodu macierzystego, który uzyskuje dostęp do fizycznego rejestry procesora. **Rejestruje** jest wyświetlana w oknie tych fizycznych rejestrów dla środowiska uruchomieniowego języka wspólnego lub kodu natywnego. **Rejestruje** okna nie wyświetla informacji rejestru dla skryptu lub aplikacji programu SQL, ponieważ skrypt i SQL są języki, które nie obsługują koncepcję rejestrów.  
  
 Aby uzyskać więcej informacji na temat wyświetlania **rejestruje** okna, zobacz [korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md).  
  
 Podczas przeglądania **rejestruje** okna, zobaczysz wpisy, np. w tym przykładzie:  
  
```  
EAX = 003110D8  
```  
  
 Symbol po lewej stronie znaku = jest nazwa rejestru EAX, w tym przypadku. Liczba po prawej stronie znaku = reprezentuje zawartość rejestru.  
  
 **Rejestruje** okna umożliwia wykonywanie więcej niż tylko widok zawartości rejestru. Podczas pracy w trybie przerwania w kodzie natywnym, można kliknąć zawartości rejestru i przejdź do edycji wartości. To nie jest coś, co należy zrobić w losowo wybranym momencie. Chyba że rozumiesz, rejestru, który edytujesz i dane, które zawiera, w wyniku edycji nieostrożnej prawdopodobnie awarię programu lub niepożądane skutki. Niestety szczegółowy opis zestawów rejestru dla różnych procesorów firmy Intel i zgodnego z Intel wykraczają daleko poza zakres to krótkie wprowadzenie.  
  
## <a name="register-groups"></a>Grup rejestru  
 Aby zwiększyć czytelność, **rejestruje** okna organizuje rejestrów w grupach. Jeśli możesz kliknąć prawym przyciskiem myszy **rejestruje** okna, pojawi się menu podręczne zawierające listę grup, które można wyświetlić lub ukryć zgodnie z potrzebami.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)
