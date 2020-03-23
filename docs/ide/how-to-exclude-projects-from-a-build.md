---
title: 'Jak: Wykluczanie projektów z kompilacji'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a19c49482c45aa0a3cf5d7cb33eb106adb65b83b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114806"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Jak: Wykluczanie projektów z kompilacji

Można utworzyć rozwiązanie bez tworzenia wszystkich projektów, które zawiera. Na przykład można wykluczyć projekt, który przerywa kompilacji. Następnie można utworzyć projekt po zbadaniu i rozwiązaniu problemów.

Projekt można wykluczyć, stosując następujące podejścia:

- Usunięcie go tymczasowo z aktywnej konfiguracji rozwiązania.

- Tworzenie konfiguracji rozwiązania, która nie obejmuje projektu.

Aby uzyskać więcej informacji, zobacz [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Aby tymczasowo usunąć projekt z aktywnej konfiguracji rozwiązania

1. Na pasku menu wybierz pozycję **Build** > **Configuration Manager**.

2. W **tabeli Konteksty projektu** zlokalizuj projekt, który chcesz wykluczyć z kompilacji.

3. W kolumnie **Kompilacja** dla projektu wyczyść to pole wyboru.

4. Wybierz przycisk **Zamknij,** a następnie odbuduj rozwiązanie.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Aby utworzyć konfigurację rozwiązania wykluczające projekt

1. Na pasku menu wybierz pozycję **Build** > **Configuration Manager**.

2. Na liście **Konfiguracja rozwiązania Active** wybierz pozycję ** \<Nowy>**.

3. W polu **Nazwa** wprowadź nazwę konfiguracji rozwiązania.

4. Na liście **Kopiuj ustawienia z** wybierz konfigurację rozwiązania, na której chcesz oprzeć nową konfigurację (na przykład **Debug),** a następnie wybierz przycisk **OK.**

5. W oknie dialogowym **Menedżer konfiguracji** wyczyść pole wyboru w kolumnie **Kompilacja** dla projektu, który chcesz wykluczyć, a następnie wybierz przycisk **Zamknij.**

6. Na **pasku** narzędzi Standardowy sprawdź, czy nowa konfiguracja rozwiązania jest aktywną konfiguracją w polu **Konfiguracje rozwiązań.**

7. Na pasku menu wybierz pozycję **Build** > **Rebuild Solution**.

## <a name="skipped-projects"></a>Pominięte projekty

Projekty mogą być pomijane podczas kompilacji, ponieważ nie są aktualne lub ponieważ są wykluczone z konfiguracji. Visual Studio używa MSBuild do tworzenia projektów. MSBuild tworzy obiekt docelowy tylko wtedy, gdy dane wyjściowe są starsze niż dane wejściowe, zgodnie z ustaleniami sygnatur czasowych pliku. Aby wymusić przebudowę, należy użyć polecenia **Build** > **Rebuild Solution**.

W okienku **kompilacji** okna **Dane wyjściowe** visual studio raportuje liczbę projektów, które były aktualne, liczbę, która została pomyślnie skompilowana, liczbę, która nie powiodła się i liczbę, które zostały pominięte. Pominięta liczba nie obejmuje projektów, które nie zostały zbudowane, ponieważ były aktualne. Gdy projekty są wykluczone z aktywnej konfiguracji, są pomijane podczas kompilacji. W danych wyjściowych kompilacji zostanie wyświetlony komunikat informujący, że projekt jest pomijany:

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Aby dowiedzieć się, dlaczego projekt został pominięty,`Debug x86` zanotuj aktywną konfigurację (w poprzednim przykładzie) i wybierz polecenie **Build** > Configuration**Manager**. Można wyświetlić lub zmienić, które projekty są pomijane dla każdej konfiguracji, jak omówiono w tym artykule.

## <a name="see-also"></a>Zobacz też

- [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)
- [Jak: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [Jak: Tworzenie wielu konfiguracji jednocześnie](../ide/how-to-build-multiple-configurations-simultaneously.md)
