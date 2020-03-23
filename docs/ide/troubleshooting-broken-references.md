---
title: Rozwiązywanie problemów z przerwanymi odwołaniami
ms.date: 03/21/2017
ms.topic: troubleshooting
helpviewer_keywords:
- C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5116d2487ca9f53c460e1cae8f362f3ff1bcdf8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565919"
---
# <a name="troubleshoot-broken-references"></a>Rozwiązywanie problemów z przerwanymi odwołaniami

Jeśli aplikacja próbuje użyć przerwanego odwołania, generowany jest błąd wyjątku. Niemożność znalezienia składnika, do którego istnieje odwołanie, jest głównym wyzwalaczem błędu, ale istnieje kilka sytuacji, w których odwołanie można uznać za przerwane. Te wystąpienia są wyświetlane na następującej liście:

- Ścieżka referencyjna projektu jest niepoprawna lub niekompletna.

- Plik, do którego istnieje odwołanie, został usunięty.

- Zmieniono nazwę pliku, do którego się odwołuje.

- Połączenie sieciowe lub uwierzytelnianie nie powiodło się.

- Odwołanie jest do składnika COM, który nie jest zainstalowany na komputerze.

Poniżej przedstawiono środki zaradcze w związku z tymi problemami.

> [!NOTE]
> Pliki w zestawach są odwoływane ze ścieżkami bezwzględnymi w pliku projektu. W związku z tym jest możliwe dla użytkowników, którzy pracują w środowisku wielozespołowym brakuje zestawu, do którego istnieje odwołanie w ich środowisku lokalnym. Aby uniknąć tych błędów, lepiej jest w tych przypadkach dodać odwołania do projektu. Aby uzyskać więcej informacji, zobacz [Programowanie za pomocą zestawów](/dotnet/framework/app-domains/programming-with-assemblies).

## <a name="reference-path-is-incorrect"></a>Ścieżka referencyjna jest niepoprawna

Jeśli projekty są współużytkowane na różnych komputerach, niektóre odwołania mogą nie zostać znalezione, gdy składnik znajduje się w innym katalogu na każdym komputerze. Odwołania są przechowywane pod nazwą pliku składnika (na przykład *MyComponent*). Po dodaniu odwołania do projektu, lokalizacja folderu pliku składnika (na przykład *C:\MyComponents)* jest dołączana do właściwości projektu **Programu ReferencePath.**

Po otwarciu projektu próbuje zlokalizować te pliki składników, do których istnieje odwołanie, patrząc w katalogach na ścieżce odniesienia. Jeśli projekt jest otwarty na komputerze, na który przechowuje składnik w innym katalogu, takim jak *D:\MyComponents,* nie można odnaleźć odwołania i pojawi się błąd na **liście zadań**.

Aby rozwiązać ten problem, można usunąć przerwane odwołanie, a następnie zastąpić je za pomocą okna dialogowego **Dodawanie odwołania.** Innym rozwiązaniem jest użycie elementu **Ścieżka odwołania na** stronach właściwości projektu i zmodyfikowanie folderów na liście, aby wskazać poprawne lokalizacje. Właściwość **Ścieżka odwołania** jest zachowywana dla każdego użytkownika na każdym komputerze. W związku z tym modyfikowanie ścieżki odwołania nie ma wpływu na innych użytkowników projektu.

> [!TIP]
> Odwołania do projektu nie mają tych problemów. Z tego powodu użyj ich zamiast odwołań do plików, jeśli to możliwe.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Aby naprawić przerwane odwołanie do projektu, korygując ścieżkę odniesienia

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i kliknij polecenie **Właściwości**.

   Pojawi się **projektant projektu.**

1. Jeśli używasz języka Visual Basic, wybierz stronę **Odwołania** i kliknij przycisk **Ścieżki odwołań.** W oknie dialogowym **Ścieżki odwołań** wpisz ścieżkę folderu zawierającego element, do którego chcesz się odwołać, w polu **Folder,** a następnie kliknij przycisk **Dodaj folder.**

    Jeśli używasz języka C#, wybierz stronę **Ścieżki odwołań.** W polu **Folder** wpisz ścieżkę folderu zawierającego element, do którego chcesz się odwołać, a następnie kliknij przycisk **Dodaj folder.**

## <a name="referenced-file-has-been-deleted"></a>Plik, do którego istnieje odwołanie, został usunięty

Możliwe, że plik, do którego istnieje odwołanie, został usunięty i nie istnieje już na dysku.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Aby naprawić przerwane odwołanie do projektu dla pliku, który już nie istnieje na dysku

- Usuń odwołanie.

- Jeśli odwołanie istnieje w innej lokalizacji na komputerze, przeczytaj je z tej lokalizacji.

## <a name="referenced-file-has-been-renamed"></a>Nazwa pliku, do którego istnieje odwołanie, została zmieniona

Możliwe, że nazwa pliku, do którego istnieje odwołanie, została zmieniona.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Aby naprawić przerwane odwołanie do pliku, którego nazwa została zmieniona

- Usuń odwołanie, a następnie dodaj odwołanie do pliku o zmienionej nazwie.

- Jeśli odwołanie istnieje w innej lokalizacji na komputerze, należy odczytać je z tej lokalizacji.

## <a name="network-connection-or-authentication-has-failed"></a>Połączenie sieciowe lub uwierzytelnianie nie powiodło się

Może istnieć wiele możliwych przyczyn niedostępnych plików: na przykład nieudane połączenie sieciowe lub nieudane uwierzytelnianie. Każda przyczyna może mieć unikalny sposób odzyskiwania; na przykład może być konieczne skontaktowanie się z administratorem lokalnym w celu uzyskania dostępu do wymaganych zasobów. Jednak usunięcie odwołania i naprawienie kodu, który go używał, jest zawsze opcją.

## <a name="com-component-is-not-installed-on-computer"></a>Składnik COM nie jest zainstalowany na komputerze

Jeśli użytkownik dodał odwołanie do składnika COM, a drugi użytkownik próbuje uruchomić kod na komputerze, na który nie ma zainstalowanego tego składnika, drugi użytkownik otrzyma błąd, że odwołanie jest uszkodzony. Zainstalowanie składnika na drugim komputerze spowoduje poprawienie błędu. Aby uzyskać więcej informacji na temat używania odwołań do składników COM w projektach, zobacz [interoperacyjność COM w aplikacjach .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).

## <a name="see-also"></a>Zobacz też

- [Strona odwołań, Projektant projektu (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)
