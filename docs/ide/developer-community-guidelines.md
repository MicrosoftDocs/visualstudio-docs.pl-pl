---
title: Wytyczne od społeczności deweloperów
description: Zawiera opis wytycznych dotyczących pracy z społecznością deweloperów programu Visual Studio.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b39b62ade75687a61981712c47e9876a0ef082fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87972476"
---
# <a name="developer-community-guidelines"></a>Wytyczne od społeczności deweloperów

Społeczność deweloperów śledzi problemy i sugestie funkcji dla programu Visual Studio.

## <a name="submitting-problems-and-suggestions"></a>Przesyłanie problemów i sugestii

[Społeczność deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/) śledzi problemy i sugestie dotyczące funkcji dla programu Visual Studio.

### <a name="before-submitting-an-issue"></a>Przed przesłaniem problemu

Wyszukaj swój problem w społeczności deweloperów programu Visual Studio, aby upewnić się, że jeszcze nie istnieje. Jeśli okaże się, że problem już istnieje, wprowadź odpowiednie komentarze i Odnotuj swój głos.

Jeśli problem jest pytaniem, skontaktuj się z społecznością, aby uzyskać [Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) przy użyciu tagu _Visual-Studio_. Pracownicy działu pomocy technicznej działu IT mogą monitorować ten tag i pomóc w udzieleniu odpowiedzi na pytania.

Jeśli nie możesz znaleźć istniejącego problemu opisującego usterkę lub funkcję, Prześlij problem, korzystając z poniższych wskazówek.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>Pisanie dobrego raportu o usterce lub sugestii funkcji

- Tylko jeden problem lub żądanie funkcji dla danego problemu.

  - Łączenie wielu problemów lub żądań funkcji w ramach jednego problemu utrudnia nam zdiagnozowanie i utrudnienie innym użytkownikom głosowania w poszukiwaniu problemu.
  - Nie dodawaj problemu jako komentarz do istniejącego problemu, chyba że jest on przeznaczony dla identycznych danych wejściowych. Wiele problemów wygląda podobnie, ale ma różne przyczyny, co utrudnia nam zdiagnozowanie problemu.

- Im więcej informacji o tym, co można podać, tym łatwiej będzie w stanie odtworzyć i rozwiązać problem.
- W każdym z problemów należy uwzględnić następujące kroki.

  - Etapy odtwarzalności (1... 2... 3...) i czego oczekujesz.
  - Obrazy, animacje lub link do filmu wideo. Obrazy i animacje ilustrują Odtwórz kroki, ale _nie_ zastępują ich.
  - Zgodnie z potrzebami fragment kodu, który pokazuje problem lub link do repozytorium kodu, można łatwo ściągnąć na naszym komputerze, aby odtworzyć problem.

- Pamiętaj, aby wykonać następujące czynności:

  - Wyszukaj, aby sprawdzić, czy istnieje duplikat. Jeśli tak, zagłosuj na istniejący problem, podając dodatkowe komentarze lub wyjaśnienia w razie potrzeby.
  - Utwórz ponownie problem po wyłączeniu wszystkich rozszerzeń. Jeśli okaże się, że problem jest spowodowany przez zainstalowaną przez siebie rozszerzenie, należy odpowiednio plikować rozszerzenie.
  - Uprość swój kod wokół problemu, aby lepiej izolować ten problem.

Nawet w przypadku problemów, które zawierają szczegółowe informacje, firma Microsoft może nie być w stanie odtworzyć problemu i może podawać więcej informacji!

## <a name="managing-problem-reports"></a>Zarządzanie raportami o problemach

Segregowania problemu to wieloetapowy proces, który jest wspólnie wykonywany w ramach zespołu funkcji. Segregowania zazwyczaj trwa jeden tydzień, ale może trwać dłużej. Celem segregowania jest umożliwienie dokładnego poznania informacji o tym, co się stanie z problemem. Na przykład po Klasyfikacja się, że planujemy rozwiązać problem, lub zaczekaj na dalszą opinię społecznościową.

Po zgłoszeniu problemu Stany wskazują, gdzie Twoje zgłoszenia są w cyklu życia. Ponieważ zespoły produktów Visual Studio przeglądają swoją opinię, ustawiają ją z odpowiednim stanem. Śledź postępy raportów o problemach, odwołując się do [stanów problemów i często ZAdawanych pytań](https://docs.microsoft.com/visualstudio/ide/report-a-problem).

Gdy w przypadku problemu brakuje ważnych informacji, przypiszemy stan _więcej informacji_ . Prosimy o problem z konkretnymi informacjami, których potrzebujemy, i otrzymasz powiadomienie e-mail. Jeśli nie otrzymasz informacji w ciągu siedmiu dni, wyślemy Ci przypomnienie. Po tym czasie będziemy zamykać bilet po 14 dniach braku aktywności.

### <a name="wont-fix-bugs"></a>Nie naprawianie usterek

Niektóre usterki są zamykane w przypadku niekorzystnego zrównoważenia kosztów. Na przykład, Jeśli poprawka jest tak skomplikowana, ryzyko związane z ryzykiem IT dla wielu użytkowników, naprawianie może być nieuzasadnione. Po zamknięciu usterki w takiej sytuacji wyjaśnimy, dlaczego to zrobimy.

### <a name="other-product"></a>Inny produkt

Czasami podczas zgłaszania problemu zostaje on spowodowany przez inny produkt, a nie program Visual Studio. Może to być inna powiązana aplikacja lub rozszerzenie. 

Gdy tak się stanie, zamknie problem i poprosił Cię o otwarcie go przy użyciu innego produktu. Poniżej przedstawiono niektóre typowe miejsca, w których można nawiązać te problemy:

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Obsługa Visual Studio Subscription](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Dodatkowe informacje

- [Jak zwiększyć szanse na rozwiązywanie problemów z wydajnością](https://docs.microsoft.com/visualstudio/ide/how-to-increase-chances-of-performance-issue-being-fixed)
- [Rozwiązywanie problemów i Tworzenie dzienników dla programu MSBuild](https://docs.microsoft.com/visualstudio/ide/msbuild-logs)

## <a name="managing-feature-suggestions"></a>Zarządzanie sugestiami funkcji

Sugestie dotyczące funkcji są sposobem komunikacji między nami i członkami społeczności deweloperów. Technicznie możemy pozostawić wszystkie żądania funkcji otwarte w nieskończoność. Jednak utrzymywanie otwartych problemów zmniejsza widoczność społeczności do rzeczywistego stanu funkcji. W _związku z tym_ będziemy zamykać żądania funkcji, które nie są adresami i przypisująmy do nich funkcje, które możemy zająć do tej etykiety.

Jeśli zaproponujesz funkcję, możesz zrezygnować z wywieszania, że nie zamierzamy zająć się Twoim żądaniem. Rozumiemy, że. Wszystkie stany USA zostały już wprowadzone w tym projekcie lub przez innych użytkowników. Dzięki temu polubimy wszystkie Twoje dane wejściowe. Nie pobieraj osobistych OFFENSE, gdy zamkniesz lub przypiszesz etykietę _Recenzja_ do swojej sugestii. Jeśli uważasz, że twoja sugestia funkcji zasługuje na otwarte, Wyjaśnij swój przypadek użycia i skontaktuj się z nami lub Zbierz więcej głosów.

W naszym procesie podejmowania decyzji Przyjrzyjmy się następującej charakterystyce dotyczącej sugestii funkcji:

- Czy jest ono zgodne z naszym ogólnym kierownictwem produktu?
- Czy możemy stworzyć i obsługiwać ją?
- Czy jest ono zgodne z naszą ogólną strategią [planu](https://docs.microsoft.com/visualstudio/productinfo/vs-roadmap) ?
- Czy dział IT ma pomoc techniczną, jak wskazuje głosy i Komentarze?
- Podoba nam się to, nawet w przypadku niskich wsparcia dla społeczności?

Jeśli nie możemy odpowiedzieć na żadne z tych pytań, zostanie ono zamknięte. Jednak często sugestia pozostanie otwarta w _ramach przeglądu_ , aby zebrać więcej opinii społeczności.

Jeśli sugestia nie jest zgodna z naszym ogólnym kierunkiem produktu, zostanie ona ZAMKNIĘTA *poza zakresem*. Na przykład firma Microsoft może mieć podobne inwestycje w innych członków rodziny produktów Visual Studio. Lub Sugerowana funkcja może być przeznaczona tylko dla kilku osób, dzięki czemu rozszerzenie jest lepiej dopasowane do jego udostępniania.

Śledź postęp swojej sugestii dotyczących funkcji, odwołując się do [Stanów sugestii i często ZAdawanych pytań](https://docs.microsoft.com/visualstudio/ide/report-a-problem).

## <a name="discussion-etiquette"></a>Zaleceniami dotyczącymi tworzenia dyskusji

Aby zachować konwersację jasno i nieprzezroczystą, Ogranicz dyskusję do języka angielskiego i zadbaj o to, aby zachować problemy. Considerate się z innymi osobami i zawsze staraj się, aby courteous i Professional.

Aby uzyskać więcej informacji, zobacz Kodeks [postępowania firmy Microsoft dla społeczności](https://answers.microsoft.com/en-us/page/codeofconduct).

Wszelkie naruszenia zaleceniami dotyczącymi tworzenia dyskusji mogą prowadzić do usunięcia komentarza i ostatecznie zakazywanie użytkownika.

## <a name="data-privacy"></a>Prywatność danych

Komentarze i odpowiedzi są publicznie widoczne, ale wszystkie dołączone pliki są udostępniane prywatnie tylko z firmą Microsoft. Ta widoczność jest korzystna, ponieważ umożliwia całej społeczności przeglądanie problemów i rozwiązań znalezionych przez innych użytkowników. Jeśli obawiasz się o prywatność Twoich danych lub tożsamości, możesz korzystać z opcji. Przeczytaj więcej o [ochronie prywatności danych społeczności deweloperów](https://docs.microsoft.com/visualstudio/ide/developer-community-privacy).

## <a name="next-steps"></a>Następne kroki

Przejdź do [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/) , aby zgłosić problemy, zasugerować funkcje lub przejrzeć istniejące bilety. Owocnej pracy.
