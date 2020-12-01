---
title: Jak mogę przypisać subskrypcje programu Visual Studio?
description: Subskrypcje można przypisywać użytkownikom końcowym pojedynczo lub za pomocą funkcji dodawania zbiorczego, która umożliwia szybkie i łatwe przekazywanie większej...
ms.faqid: group1_3
ms.topic: include
ms.assetid: 59eb35fd-ec94-41ce-b24c-a8a120976bac
author: CaityBuschlen
ms.author: cabuschl
ms.date: 09/30/2020
ms.openlocfilehash: add0bac2a9e7eb053c183d66fcee17c8133bb921
ms.sourcegitcommit: 593bdd2da62633f8d1f1eef70d0238e2682f3e02
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2020
ms.locfileid: "91838449"
---
## <a name="how-do-i-assign-visual-studio-subscriptions"></a>Jak mogę przypisać subskrypcje programu Visual Studio?

Subskrypcje można przypisywać użytkownikom końcowym pojedynczo lub za pomocą funkcji dodawania zbiorczego, która umożliwia szybkie i łatwe przekazywanie większej liczby subskrybentów jednocześnie.

Aby przypisać subskrypcje pojedynczo:

1. Wybierz [kartę Zarządzanie subskrybentami](https://manage.visualstudio.com/subscribers) w górnej części strony [manage.visualstudio.com](https://manage.visualstudio.com)
2. Wybierz pozycję Dodaj i wpisz nazwę i adres e-mail użytkownika, do którego chcesz przypisać subskrypcję.
    1. Jeśli w Twojej organizacji jest używana usługa Azure Active Directory, w polu Nazwa będą wyszukiwane osoby w bieżącym katalogu. Możesz wybrać pozycję z wyników wyszukiwania lub dodać osobę ręcznie.
3. Jeśli chcesz, aby subskrybent miał dostęp do oprogramowania do pobrania po zalogowaniu w [portalu subskrypcji programu Visual Studio](https://my.visualstudio.com/), upewnij się, że przełącznik umożliwiający pobieranie plików w sekcji Ustawienia pobierania jest włączony.
4. Uzupełnij sekcję Preferencje komunikacji, aby określić, w jakim języku wysłać subskrybentom wiadomość e-mail z powiadomieniem o przypisaniu.
5. Jeśli chcesz dodać notatki powiązane z przypisaniem, zaznacz pole Dokumentacja.
6. Wybierz pozycję Dodaj w dolnej części panelu wysuwanego, aby zakończyć przypisywanie subskrypcji. Subskrybent otrzyma wiadomość e-mail i będzie mógł natychmiast rozpocząć korzystanie z subskrypcji programu Visual Studio (nie musi aktywować subskrypcji).

Aby przypisać subskrypcje zbiorczo:

1. Wybierz [kartę Zarządzanie subskrybentami](https://manage.visualstudio.com/subscribers) w górnej części strony [manage.visualstudio.com](https://manage.visualstudio.com).
2. Wybierz pozycję Dodawanie zbiorcze, pobierz szablon programu Excel i zapisz kopię lokalną.
3. Musisz uzupełnić wszystkie pola oprócz pola Dokumentacja.
    1. Sprawdź, czy żadne z pól formularza nie zawiera przecinków.
    2. Usuń spacje przed polami formularza i po nich.
    3. Sprawdź, czy nazwy nie zawierają dodatkowych spacji pomiędzy częściami imienia lub nazwiska (jeśli na przykład użytkownik ma dwuczęściowe imię „Maggie May” należy wpisać „MaggieMay”).
4. Wróć do strony [manage.visualstudio.com](https://manage.visualstudio.com), wybierz pozycję Dodawanie zbiorcze i przekaż zapisaną kopię szablonu programu Excel.
5. Po pomyślnym przekazaniu zostanie wyświetlona strona z potwierdzeniem, a nowi subskrybenci będą widoczni na liście subskrybentów. Subskrybenci otrzymają wiadomość e-mail i będą mogli natychmiast rozpocząć korzystanie z subskrypcji programu Visual Studio (nie muszą aktywować subskrypcji).

[Przeczytaj informacje](https://docs.microsoft.com/visualstudio/subscriptions/assign-license#add-a-single-subscriber) dotyczące przypisywania subskrypcji w portalu administratora subskrypcji programu Visual Studio, aby dowiedzieć się więcej na temat szybkiego i łatwego przypisywania subskrypcji.  [Dowiedz się więcej](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) o zarządzaniu subskrypcjami programu Visual Studio z usługą GitHub Enterprise. 

## <a name="what-is-the-github-enterprise-setup-process"></a>Jaki jest proces konfigurowania usługi GitHub Enterprise? 

Usługa GitHub Enterprise jest konfigurowana i zarządzana niezależnie od subskrypcji programu Visual Studio. Po zakupie programu Visual Studio z usługą GitHub Enterprise inicjowany jest proces konfigurowania konta w usłudze GitHub Enterprise, który odbywa się równolegle z zawarciem umowy w witrynie manage.visualstudio.com (ale oddzielnie). Ustanowienie tego konta usługi GitHub Enterprise może trochę potrwać.  

Gdy firma skonfiguruje konto usługi GitHub Enterprise, subskrybenci, którym przypisano subskrypcje programu Visual Studio z usługą GitHub Enterprise, otrzymają wiadomość e-mail od usługi GitHub z powiadomieniem o połączeniu ich subskrypcji programu Visual Studio. Po otrzymaniu tej wiadomości e-mail subskrybenci mogą skontaktować się ze swoim administratorem organizacji w usłudze GitHub, aby otrzymać zaproszenie do odpowiedniej organizacji. 

[Dowiedz się więcej](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) o zarządzaniu subskrypcjami programu Visual Studio z usługą GitHub Enterprise. Zapoznaj się z [dokumentacją dotyczącą subskrybentów](https://docs.microsoft.com/visualstudio/subscriptions/access-github), aby uzyskać dodatkowe informacje na temat procesu konfigurowania usługi GitHub Enterprise. 