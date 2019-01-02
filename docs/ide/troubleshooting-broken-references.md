---
title: Rozwiązywanie problemów z przerwanymi odwołaniami
ms.date: 03/21/2017
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c4d45dc01201747240f2ebbc50854b77fd31ec0f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847129"
---
# <a name="troubleshoot-broken-references"></a>Rozwiązywanie problemów z przerwanymi odwołaniami

Jeśli aplikacja próbuje użyć uszkodzone odwołanie, generowany jest błąd wyjątku. Z brakiem, aby odnaleźć składnika, do którego istnieje odwołanie jest podstawowym wyzwalacza dla błędu, ale istnieje kilka sytuacji, w których odwołanie jest uznawana za uszkodzone. Te wystąpienia są wyświetlane na poniższej liście:

- Ścieżka odwołania projektu jest niepoprawne lub niepełne.

- Usunięto plik, do którego nastąpiło odwołanie.

- Zmieniono nazwę pliku, którego dotyczy odwołanie.

- Połączenie sieciowe lub uwierzytelnianie nie powiodło się.

- Odwołanie jest składnika modelu COM, który nie jest zainstalowany na komputerze.

Dostępne są następujące środki zaradcze tych problemów.

> [!NOTE]
> Pliki w zestawach są przywoływane przy użyciu ścieżek bezwzględnych w pliku projektu. Dlatego jest możliwe dla użytkowników, którzy pracują w środowisku projektowanie brakuje przywoływanego zestawu w środowisku lokalnym. Aby uniknąć tych błędów, lepiej jest w takich przypadkach można dodać odwołania projektu do projektu. Aby uzyskać więcej informacji, zobacz [programowanie za pomocą zestawów](/dotnet/framework/app-domains/programming-with-assemblies).

## <a name="reference-path-is-incorrect"></a>Ścieżka odwołania jest nieprawidłowy

Jeśli projekty są współdzielone na różnych komputerach, niektóre odwołania nie będzie można znaleźć gdy składnik znajduje się w innym katalogu na każdym komputerze. Odwołania są przechowywane w nazwie pliku składnika (na przykład *MyComponent*). Po dodaniu odwołania do projektu, lokalizacja folderu pliku składnika (na przykład *C:\MyComponents*) jest dołączany do **ReferencePath** właściwość projektu.

Po otwarciu projektu próbuje zlokalizować te pliki składnika przez wyszukiwanie w katalogach w ścieżce odwołania. Jeśli projekt jest otwierany na komputerze, na którym są przechowywane składnika w innym katalogu, takie jak *D:\MyComponents*, nie można odnaleźć odwołania i pojawia się błąd w **listy zadań**.

Aby rozwiązać ten problem, możesz usunąć uszkodzone odwołanie, a następnie zastąp go za pomocą **Dodaj odwołanie** okno dialogowe. Innym rozwiązaniem jest użycie **ścieżkę odwołania** elementów na stronach właściwości projektu i zmodyfikować foldery na liście, aby wskazywał poprawne lokalizacje. **Ścieżkę odwołania** właściwość jest trwały dla każdego użytkownika na każdym komputerze. W związku z tym modyfikując ścieżki odniesienia nie ma wpływu na innych użytkowników projektu.

> [!TIP]
> Odwołania projekt projekt nie ma tych problemów. Z tego powodu ich używać zamiast odwołania do pliku, jeśli to możliwe.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Aby naprawić uszkodzone odwołanie, poprawiając ścieżkę odwołania

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i kliknij przycisk **właściwości**.

   **Projektanta projektu** pojawia się.

1. Jeśli używasz języka Visual Basic, wybierz opcję **odwołania** strony, a następnie kliknij przycisk **ścieżki odwołania** przycisku. W **ścieżki odwołania** okna dialogowego wpisz ścieżkę do folderu, który zawiera element, którego chcesz się odwołać w **folderu** pola, a następnie kliknij przycisk **Dodaj Folder** przycisku.

    Jeśli używasz C#, wybierz opcję **ścieżki odwołania** strony. W **folderu** wpisz ścieżkę do folderu, który zawiera element, który chcesz odwołać, a następnie kliknij przycisk **Dodaj Folder** przycisku.

## <a name="referenced-file-has-been-deleted"></a>Przywoływany plik został usunięty.

Jest to możliwe, że plik, do którego nastąpiło odwołanie, został usunięty i już nie istnieje na dysku.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Aby naprawić przerwane odwołanie do pliku, który już nie istnieje na dysku

- Usuń odwołanie.

- Jeśli istnieje odwołanie w innej lokalizacji na komputerze, należy go odczytywać z tej lokalizacji.

## <a name="referenced-file-has-been-renamed"></a>Nazwa pliku została zmieniona

Istnieje możliwość, że zmieniono nazwę pliku, którego dotyczy odwołanie.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Aby naprawić uszkodzone odwołanie do pliku, którego nazwa została zmieniona

- Usuń odwołanie, a następnie dodaj odwołanie do pliku o zmienionej nazwie.

- Odwołanie istnieje w innej lokalizacji na komputerze, należy go odczytywać z tej lokalizacji.

## <a name="network-connection-or-authentication-has-failed"></a>Połączenie sieciowe lub uwierzytelnianie nie powiodło się

Może istnieć wiele możliwe przyczyny niedostępności plików: połączenie sieciowe nie powiodło się lub niepowodzenie uwierzytelniania, na przykład. Przyczyny dotyczyły, może być unikatowy oznacza, że odzyskiwania; na przykład może być konieczne skontaktuj się z administratorem lokalnym w celu dostępu do wymaganych zasobów. Jednak usunięcie odwołania i naprawianie kodu, których jej jest zawsze opcję.

## <a name="com-component-is-not-installed-on-computer"></a>Składnik COM nie jest zainstalowany na komputerze

Jeśli użytkownik doda odwołanie do składnika modelu COM, a drugi użytkownik próbuje uruchomić kod na komputerze, na którym nie zainstalowano tego składnika, drugi użytkownik zostanie wyświetlony błąd, czy odwołanie jest uszkodzony. Instalowanie składnika na drugim komputerze spowoduje Popraw błąd. Aby uzyskać więcej informacji o sposobie używania odwołania do składników modelu COM w projektach, zobacz [współdziałanie COM w aplikacjach .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).

## <a name="see-also"></a>Zobacz także

- [Strona odwołań, Projektant projektu (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)