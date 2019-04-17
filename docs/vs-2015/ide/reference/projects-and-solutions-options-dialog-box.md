---
title: Projekty i rozwiązania, okno dialogowe Opcje | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9c4876aedd12b2284982304b16049691ce6c9b0d
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652894"
---
# <a name="projects-and-solutions-options-dialog-box"></a>Opcje projektów i rozwiązań — okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ustawia domyślną ścieżkę [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] folderów projektu i określa domyślne zachowanie **dane wyjściowe** oknie **listy zadań**, i **Eksploratora rozwiązań** jako projekty są opracowane i wbudowane. Aby otworzyć to okno dialogowe, kliknij przycisk **narzędzia / Opcje** rozwiń **projekty i rozwiązania**i kliknij przycisk **ogólne**.  
  
> [!NOTE]
>  Dostępne opcje w oknach dialogowych i nazwy i lokalizacje poleceń menu, który zostanie wyświetlony, mogą różnić się od opisanych w pomocy, w zależności od ustawień aktywnych lub wersji. Ta strona pomocy został napisany z **ogólne ustawienia projektowe** na uwadze. Aby wyświetlić lub zmienić ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="settings"></a>Ustawienia  
 **Lokalizacja projektów**  
 Ustawia domyślną lokalizację, w którym są tworzone nowe projekty i rozwiązania folderów i katalogi. Kilka okien dialogowych również użyć lokalizacji zestawu w przypadku tej opcji dla folderu punktów początkowych. Na przykład okno dialogowe Otwórz projekt korzysta z tej lokalizacji dla skrótu Moje projekty.  
  
 **Lokalizacja szablonów projektów użytkownika**  
 Ustawia domyślną lokalizację, która jest używana przez **nowy projekt** okno dialogowe, aby utworzyć listę **Moje szablony**. Aby uzyskać więcej informacji, zobacz [jak: Lokalizowanie i organizacja szablonów](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Lokalizacja szablonów elementów użytkownika**  
 Ustawia domyślną lokalizację, która jest używana przez **Dodaj nowy element** okno dialogowe, aby utworzyć listę **Moje szablony**. Aby uzyskać więcej informacji, zobacz [jak: Lokalizowanie i organizacja szablonów](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Zawsze pokazuj lista błędów Jeżeli kompilacja zakończy się z błędami**  
 Otwiera **lista błędów** okna po zakończeniu kompilacji, tylko wtedy, gdy nie można skompilować projektu. Błędy występujące podczas procesu kompilacji są wyświetlane. Gdy ta opcja jest wyczyszczone, nadal występują błędy, ale nie można otworzyć okna po zakończeniu kompilacji. Ta opcja jest domyślnie włączona.  
  
 **Śledź aktywny element w Eksploratorze rozwiązań**  
 Po wybraniu **Eksploratora rozwiązań** automatycznie zostanie otwarty i aktywny element jest wybrany. Zmiany wybranego elementu, jak pracować z różnych plików w projekcie lub rozwiązaniu lub różne składniki w projektancie. Jeśli ta opcja jest wyczyszczone, zaznaczenie w **Eksploratora rozwiązań** nie zmienia się automatycznie. Ta opcja jest domyślnie włączona.  
  
 **Pokaż zaawansowane konfiguracje kompilacji**  
 Po wybraniu opcji konfiguracji kompilacji są wyświetlane na **strony właściwości projektu** okno dialogowe i **strony właściwości rozwiązania** okno dialogowe. Po wyczyszczeniu, opcji konfiguracji kompilacji nie są wyświetlane na **strony właściwości projektu** okno dialogowe i **strony właściwości rozwiązania** okno dialogowe [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] i [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projektów zawierające jedną konfigurację lub dwie konfiguracje debugowania, jak i wydania. Jeśli projekt ma konfigurację zdefiniowanych przez użytkownika, są wyświetlane opcje konfiguracji kompilacji.  
  
 Jeśli usunięto zaznaczenie, polecenia na **kompilacji** menu, takich jak **Kompiluj rozwiązanie**, **Kompiluj rozwiązanie**, i **czyste rozwiązanie**, są wykonywane w konfiguracji wydania i poleceń na **debugowania** menu, takich jak **Rozpocznij debugowanie** i **Rozpocznij bez debugowania**, są wykonywane na Konfiguracja debugowania.  
  
 **Zawsze pokazuj rozwiązanie**  
 Po wybraniu rozwiązania i wszystkich poleceń, które działają w rozwiązaniach są zawsze wyświetlane w środowisku IDE. Po wyczyszczeniu, wszystkie projekty są tworzone jako autonomiczny projekty i rozwiązania w Eksploratorze rozwiązań lub poleceń, które działają nie jest wyświetlany w rozwiązania w środowisku IDE, jeśli rozwiązanie zawiera tylko jeden projekt.  
  
 **Zapisz nowe projekty po utworzeniu**  
 Po wybraniu, można określić lokalizację dla projektu w **nowy projekt** okno dialogowe. Po wyczyszczeniu, wszystkie nowe projekty są tworzone jako projektów tymczasowych. Podczas pracy z projektami tymczasowej, można tworzyć i eksperymentować z projektem, bez konieczności określania lokalizacji na dysku.  
  
 **Ostrzegaj użytkownika, gdy lokalizacja projektu nie jest zaufana**  
 Jeśli spróbujesz utworzyć nowy projekt lub Otwórz istniejący projekt w lokalizacji, która nie jest w pełni zaufany (na przykład na ścieżkę UNC lub ścieżki HTTP), zostanie wyświetlony komunikat. Użyj tej opcji, aby określić, czy komunikat jest wyświetlany za każdym razem, spróbuj utworzyć lub otworzyć projekt w lokalizacji, która nie jest w pełni zaufany.  
  
 **Pokaż okno dane wyjściowe, gdy rozpoczyna się kompilacja**  
 Automatycznie wyświetla okno danych wyjściowych w środowisku IDE na początku rozwiązania kompilacji. Aby uzyskać więcej informacji, zobacz [jak: Kontrolowanie okna danych wyjściowych](http://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858). Ta opcja jest domyślnie włączona.  
  
 **Monituj o symboliczną zmianę nazwy podczas zmieniania nazw plików**  
 Po wybraniu wyświetla komunikat dialogowe z pytaniem, czy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] również należy zmienić wszystkie odwołania w projekcie do elementu kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Okno dialogowe Opcje, Projekty i rozwiązania, Kompilowanie i uruchamianie](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
