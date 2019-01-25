---
title: Zapewnianie dostępu do VBA do utworzenia lub otwarcia Visual Studio Tools dla programu Microsoft Office project system
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1d95f3915cb3c8bd780247655058fdc9dd908df2
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869362"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Zapewnianie dostępu do VBA do utworzenia lub otwarcia Visual Studio Tools dla programu Microsoft Office project system

Musisz jawnie włączyć dostęp do programu Visual Basic for Applications (VBA) system projektu w programie Microsoft Office, można było utworzyć lub otworzyć Visual Studio Tools dla programu Microsoft Office project system.

 Projektów deweloperskich Microsoft Office wymagają dostępu do języka Visual Basic for Applications (VBA) system projektu w programie Microsoft Office Word i Microsoft Office Excel, nawet jeśli projekty nie należy używać języka Visual Basic dla aplikacji. Obsługi w czasie projektowania formanty zarówno języka Visual Basic i C# projektów zależy od języka Visual Basic for Applications systemu projektu.

 Microsoft Office wirusów makr próba Automatyzacja języka Visual Basic for Applications systemu projektu jako środek do propagowania samodzielnie. Dzięki dostępowi do języka Visual Basic dla aplikacji, system projektu, należy usunąć ochronę, która pomaga zapobiegać rozprzestrzeniania się wirusów makr. Jednak zabezpieczeń makr normalne pozostaje w miejscu, dzięki czemu poziomu zabezpieczeń makr i listę zaufanych wydawców, obsługa dla aplikacji pakietu Office, które określi, czy dowolne makro jest uruchamiana na komputerze.

> [!NOTE]
> Dotyczy to tylko na komputerze deweloperskim. Komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office po włączeniu tej opcji nie jest konieczne.

 Należy pamiętać, że wyłączenie dostępu do języka Visual Basic dla aplikacji, system projektu na swój własny nie chronią przed wirusami, ale po prostu przestanie wirusów rozprzestrzenianiu się do innych dokumentów, jeśli komputer staje się coraz zainfekowany za pomocą makra Aplikacje antywirusowe. Opcja jest domyślnie wyłączona, jako dodatkową warstwę ochrony dla komputera, ale jej włączeniu nie wprowadzać na komputerze więcej podatny na wirusy Jeśli postępujesz zgodnie z najlepszych rozwiązań dotyczących zabezpieczeń.

 Najlepszą ochronę przed wirusami jest uruchomienie pakietu Office w dużej lub bardzo wysoki poziom zabezpieczeń, tylko ufać makra z weryfikacji, znanych źródeł, pakietu Office i na bieżąco, za pomocą poprawek zabezpieczeń i programy antywirusowe.

 Aby uzyskać więcej informacji na temat ochrony komputera przed wirusami i innych złośliwego kodu, zobacz [ http://www.microsoft.com/protect ](http://www.microsoft.com/protect).

 Można włączyć lub wyłączyć opcję **zaufania dostęp do projektu języka Visual Basic** ręcznie.

 Jeśli widzisz błędy VBA lub COM, można naprawić instalację pakietu Office.

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Aby włączyć lub wyłączyć dostęp do projektów języka Visual Basic

1. Kliknij przycisk **pliku** kartę.

2. Kliknij przycisk **opcje**.

3. Kliknij przycisk **Centrum zaufania**, a następnie kliknij przycisk **ustawienia Centrum zaufania**.

4. W **Centrum zaufania**, kliknij przycisk **ustawienia makr**.

5. Zaznacz lub usuń zaznaczenie pola wyboru **ufają dostępu do modelu obiektu projektu VBA** Aby włączyć lub wyłączyć dostęp do projektów Visual Basic.

6. Kliknij przycisk **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Aby włączyć lub wyłączyć dostęp do projektów języka Visual Basic z systemu Microsoft Office 2007

1. Na **narzędzia** menu w programie Word lub Excel, wskaż polecenie **— makro**, a następnie kliknij przycisk **zabezpieczeń**.

2. W **zabezpieczeń** okno dialogowe, kliknij przycisk **zaufanych wydawców** kartę.

3. Zaznacz, aby włączyć lub usuń zaznaczenie, aby wyłączyć, **zaufania dostęp do projektu języka Visual Basic**.

4. Kliknij przycisk **OK**.

## <a name="to-set-your-office-macro-security-level"></a>Aby ustawić poziom zabezpieczeń makr pakietu Office

1. Kliknij przycisk **pliku** kartę.

2. Kliknij przycisk **opcje**.

3. Kliknij przycisk **Centrum zaufania**, a następnie kliknij przycisk **ustawienia Centrum zaufania**.

4. W **Centrum zaufania**, kliknij przycisk **ustawienia makr**.

5. W **ustawienia makr** wybierz odpowiednie ustawienie.

6. Kliknij przycisk **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Aby ustawić poziom zabezpieczeń makr pakietu Office przy użyciu systemu Microsoft Office 2007

1. Na **narzędzia** menu w programie Word lub Excel, wskaż polecenie **— makro**, a następnie kliknij przycisk **zabezpieczeń**.

2. Na **poziom zabezpieczeń** , a następnie wybierz odpowiednie ustawienie.

    **Poziom zabezpieczeń** karta zawiera szczegóły dotyczące poszczególnych poziomów. Aby uzyskać więcej informacji zobacz temat "Poziomy zabezpieczeń makr" w Pomocy pakietu Office.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Aby zainstalować VBA przy użyciu systemu Microsoft Office 2007

1. W Panelu sterowania, uruchom **apletu Dodaj lub usuń programy** lub **programy i funkcje**.

2. Wybieranie pakietu Office w **aktualnie zainstalowane programy** listy.

3. Kliknij przycisk **zmiany**.

4. Wybierz **apletu Dodaj lub usuń funkcje**, a następnie kliknij przycisk **Kontynuuj**.

5. Wybierz **Wybierz zaawansowane dostosowywanie aplikacji**, a następnie kliknij przycisk **dalej**.

6. Rozwiń **funkcje wspólne pakietu Office** w **wybierz opcje aktualizacji aplikacji i narzędzi** listy.

7. Otwórz menu rozwijanym obok **Visual Basic for Applications**, a następnie kliknij przycisk **Uruchom z mojego komputera**.

8. Kliknij przycisk **Kontynuuj**.

9. Kliknij przycisk **Zamknij**.

## <a name="to-repair-your-installation-of-office"></a>Aby naprawić instalację pakietu Office

1. W Panelu sterowania, uruchom **apletu Dodaj lub usuń programy** lub **programy i funkcje**.

2. Wybierz wersję pakietu Office w **aktualnie zainstalowane programy** listy.

3. Kliknij przycisk **zmiany**.

4. Wybierz **ponownej instalacji lub naprawy**, a następnie kliknij przycisk **dalej**.

5. Wybierz **Wykryj i napraw błędy instalacji pakietu Office**, a następnie kliknij przycisk **zainstalować**.

## <a name="see-also"></a>Zobacz także

 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)