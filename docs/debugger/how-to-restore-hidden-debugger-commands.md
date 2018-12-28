---
title: 'Instrukcje: Przywracanie ukrytych poleceń debugera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7686ccd303bf47d9c3ef2ba570f2f483a4145d61
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561333"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Instrukcje: Przywracanie ukrytych poleceń debugera
Podczas konfigurowania programu Visual Studio zostanie wyświetlony monit o wybranie zestawu domyślnego ustawienia środowiska IDE dla Twojego nadrzędnego języka programowania. Domyślne ustawienia IDE w przypadku niektórych języków może ukryć niektórych poleceń debugera.  
  
 Jeśli chcesz korzystać z funkcji debugera, które zostały ukryte przez domyślne ustawienia IDE, można dodać polecenie do menu, korzystając z następującej procedury.  
  
### <a name="to-restore-hidden-debugger-commands"></a>Aby Przywracanie ukrytych poleceń debugera  
  
1.  W projekcie, które są otwarte, w **narzędzia** menu, kliknij przycisk **Dostosuj**.  
  
2.  W **Dostosuj** okno dialogowe, kliknij przycisk **polecenia** kartę.  
  
3.  W **pasek Menu:** listę rozwijaną, wybierz opcję **debugowania** menu, które ma zawierać przywróconej polecenia.  
  
4.  Kliknij przycisk **Dodaj polecenie...**  przycisku.  
  
5.  W **Dodaj polecenie** wybierz polecenie, które chcesz dodać, a następnie kliknij przycisk **OK**.  
  
6.  Powtórz poprzedni krok, aby dodać inne polecenie.  
  
7.  Kliknij przycisk **Zamknij** Kiedy zakończysz dodawanie poleceń do menu.  
  
    > [!WARNING]
    >  Niektóre elementy menu są wyświetlane, gdy debuger jest w trybach określonych, takie jak tryb uruchamiania lub trybie przerwania. W związku z tym nie może być od razu widoczne element, który został dodany, po wykonaniu tych kroków.  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Przywracanie poleceń, które nie są dostępne w oknie dialogowym Dostosuj  
 Nie można przywrócić niektórych poleceń, zwłaszcza tych, które dostępnych w menu hierarchiczne z **Dostosuj** okno dialogowe. Aby przywrócić tych poleceń, należy zaimportować nową kolekcję ustawień środowiska IDE.  
  
#### <a name="to-import-new-ide-settings"></a>Aby zaimportować nowe ustawienia środowiska IDE  
  
1.  Na **narzędzia** menu, kliknij przycisk **Import i eksport ustawień**.  
  
2.  Na **Kreatora importowania i eksportowania ustawień-Zapraszamy** kliknij **Importuj ustawienia wybranego środowiska**, a następnie kliknij przycisk **dalej**.  
  
3.  Na **zapisać bieżące ustawienia** strony, zdecyduj, czy chcesz zapisać Twoje istniejące ustawienia, a następnie kliknij przycisk **dalej**.  
  
4.  Na **wybierz kolekcję ustawień do zaimportowania** w obszarze **ustawienia domyślne** folderu, wybierz kolekcję ustawień środowiska deweloperskiego, zawierający polecenia, którego chcesz użyć. Jeśli nie wiadomo, którą kolekcję, aby wybrać, spróbuj **ogólnych ustawieniach projektowych** lub **ustawienia środowiska deweloperskiego Visual C++**, które zawierają najbardziej poleceń debugera.  
  
5.  Kliknij przycisk **Dalej**.  
  
6.  Na **wybierz ustawienia do importowania** w obszarze **opcje**, upewnij się, że **debugowanie** jest zaznaczone. Wyczyść pozostałe pola wyboru, chyba że chcesz zaimportować te ustawienia, a także.  
  
7.  Kliknij przycisk **Zakończ**.  
  
8.  Na **pełny Import** przejrzyj wszelkie błędy skojarzone z Resetowanie ustawień w obszarze **szczegóły**.  
  
9. Kliknij przycisk **Zamknij**.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)