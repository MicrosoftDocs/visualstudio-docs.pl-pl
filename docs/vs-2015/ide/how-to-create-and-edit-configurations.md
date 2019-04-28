---
title: 'Instrukcje: Tworzenie i edytowanie konfiguracji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b76ad8ed6e0cc8bdf60a2053dd11106b5e03a7d1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422898"
---
# <a name="how-to-create-and-edit-configurations"></a>Instrukcje: Tworzenie i edytowanie konfiguracji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można utworzyć kilka konfiguracji kompilacji dla rozwiązania. Na przykład można skonfigurować do kompilacji debugowanej, testerom służy do znajdowania i rozwiązywania problemów i można skonfigurować różne rodzaje kompilacji, które mogą być dystrybuowane do różnych klientów.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-build-configurations"></a>Tworzenie konfiguracji kompilacji  
 Możesz użyć **programu Configuration Manager** okno dialogowe, aby wybrać lub zmodyfikuj istniejące konfiguracje kompilacji lub utworzyć nowe.  
  
#### <a name="to-open-the-configuration-manager-dialog-box"></a>Aby otworzyć okno dialogowe programu Configuration Manager  
  
- W **Eksploratora rozwiązań**, otwórz menu skrótów dla rozwiązania, a następnie wybierz **programu Configuration Manager**.  
  
  > [!NOTE]
  > Jeśli **programu Configuration Manager** polecenie nie pojawi się w menu skrótów, Szukaj w obszarze **kompilacji** menu na pasku menu. Jeśli nie pojawia się ona tam żadnego z nich, na pasku menu wybierz **narzędzia**, **opcje**, a następnie w okienku po lewej stronie **opcje** okna dialogowego rozwiń **projekty i Rozwiązania**, **ogólne**i w okienku po prawej stronie wybierz **Pokaż zaawansowane konfiguracje kompilacji** pole wyboru.  
  
   W **programu Configuration Manager** okno dialogowe, można użyć **Konfiguracja rozwiązania aktywnego** listy rozwijanej wybierz konfigurację kompilacji całego rozwiązania, zmodyfikować istniejące lub Utwórz nową Konfiguracja. Możesz użyć **aktywną platformą rozwiązania** listy rozwijanej, aby wybrać platformy, obiekty docelowe konfiguracji, zmodyfikuj istniejącą grupę lub Dodaj nową platformę. **Projektu kontekstów** okienko zawiera listę projektów w rozwiązaniu. Dla każdego projektu można wybrać konfiguracji specyficznych dla projektu i platform, zmodyfikuj istniejące, lub Utwórz nową konfigurację lub Dodaj nową platformę. Możesz również wybrać pola wyboru, które wskazują, czy każdy projekt jest dołączana w przypadku korzystania z konfiguracji całego rozwiązania do kompilacji lub wdrożenia rozwiązania.  
  
  Po skonfigurowaniu konfiguracje, które mają można ustawić właściwości projektu, które są odpowiednie dla tych konfiguracji.  
  
#### <a name="to-set-properties-based-on-configurations"></a>Aby ustawić właściwości na podstawie konfiguracji  
  
- W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.  
  
     **Stron właściwości** zostanie otwarte okno.  
  
     Można ustawić właściwości dla Twojej konfiguracji. Na przykład dla konfiguracji wydania, można określić czy kod jest zoptymalizowany, gdy rozwiązanie jest stworzone i dla konfiguracji debugowania, można określić, że `DEBUG` symbol kompilacja warunkowa jest uwzględniany. Aby uzyskać więcej informacji na temat ustawień strony właściwości, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
## <a name="creating-and-modifying-project-configurations"></a>Tworzenie i modyfikowanie konfiguracji projektu  
  
#### <a name="to-create-a-project-configuration"></a>Aby utworzyć konfigurację projektu  
  
1. Otwórz **programu Configuration Manager** okno dialogowe.  
  
2. Wybierz projekt w **projektu** kolumny.  
  
3. W **konfiguracji** listy rozwijanej dla tego projektu, wybierz **New**.  
  
     **Nowa konfiguracja projektu** zostanie otwarte okno dialogowe.  
  
4. W **nazwa** wprowadź nazwę dla nowej konfiguracji.  
  
5. Aby użyć ustawienia właściwości z istniejącej konfiguracji projektu, w **Kopiuj ustawienia** listy rozwijanej wybierz konfigurację.  
  
6. Aby utworzyć konfigurację całego rozwiązania, w tym samym czasie, zaznacz **nowa konfiguracja rozwiązania Utwórz** pole wyboru.  
  
#### <a name="to-rename-a-project-configuration"></a>Aby zmienić konfigurację projektu  
  
1. Otwórz **programu Configuration Manager** okno dialogowe.  
  
2. W **projektu** kolumnę, wybierz projekt, który ma konfigurację projektu chcesz zmienić.  
  
3. W **konfiguracji** listy rozwijanej dla tego projektu, wybierz **Edytuj**.  
  
     **Edytuj konfiguracje projektu** zostanie otwarte okno dialogowe.  
  
4. Wybierz nazwę konfiguracji projektu, który chcesz zmienić.  
  
5. Wybierz **Zmień nazwę**, a następnie wprowadź nową nazwę.  
  
## <a name="creating-and-modifying-solution-wide-build-configurations"></a>Tworzenie i modyfikowanie całego rozwiązania konfiguracje kompilacji  
  
#### <a name="to-create-a-solution-wide-build-configuration"></a>Aby utworzyć konfigurację kompilacji całego rozwiązania  
  
1. Otwórz **programu Configuration Manager** okno dialogowe.  
  
2. W **Konfiguracja rozwiązania aktywnego** listy rozwijanej wybierz **New**.  
  
     **Nowa konfiguracja rozwiązania** zostanie otwarte okno dialogowe.  
  
3. W **nazwa** tekstu wprowadź nazwę dla nowej konfiguracji.  
  
4. Aby użyć ustawień z istniejącej konfiguracji rozwiązania, w **Kopiuj ustawienia** listy rozwijanej wybierz konfigurację.  
  
5. Aby utworzyć konfiguracje projektu w tym samym czasie, należy zaznaczyć **Utwórz nowe konfiguracje projektu** pole wyboru.  
  
#### <a name="to-rename-a-solution-wide-build-configuration"></a>Aby zmienić konfigurację kompilacji całego rozwiązania  
  
1. Otwórz **programu Configuration Manager** okno dialogowe.  
  
2. W **Konfiguracja rozwiązania aktywnego** listy rozwijanej wybierz **Edytuj**.  
  
     **Edytuj konfiguracje rozwiązania** zostanie otwarte okno dialogowe.  
  
3. Wybierz nazwę konfiguracji rozwiązania, które chcesz zmienić.  
  
4. Wybierz **Zmień nazwę**, a następnie wprowadź nową nazwę.  
  
#### <a name="to-modify-a-solution-wide-build-configuration"></a>Aby zmodyfikować konfigurację kompilacji całego rozwiązania  
  
1. Otwórz **programu Configuration Manager** okno dialogowe.  
  
2. W **Konfiguracja rozwiązania aktywnego** listę rozwijaną, wybierz konfigurację ma na liście.  
  
3. W **konteksty projektu** okienko dla każdego projektu, wybierz opcję **konfiguracji** i **platformy** i wybierz opcję **kompilacji**go oraz czy **Wdróż** go.  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md)   
 [Kompilowanie oraz Oczyszczanie projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [NIB jak: Modyfikowanie właściwości projektu i ustawień konfiguracji](http://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
