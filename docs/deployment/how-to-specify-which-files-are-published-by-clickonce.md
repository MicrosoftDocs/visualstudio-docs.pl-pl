---
title: 'Instrukcje: Określanie plików publikowanych za pomocą technologii ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e11c336f891ae71968a3b325a66a50d4d9a79446
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826958"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Instrukcje: Określanie plików publikowanych za pomocą technologii ClickOnce
Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliki aplikacji, a wszystkie inne niż kod w projekcie są wdrażane wraz z aplikacji. W niektórych przypadkach mogą nie ma lub musisz opublikować określone pliki lub można zainstalować niektórych plików, na podstawie warunków. Program Visual Studio oferuje możliwości Wyklucz pliki oznaczyć pliki jako pliki danych lub wstępnie wymagane składniki oraz tworzenie grup plików dla warunkowego instalacji.  
  
 Pliki [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji są zarządzane w **pliki aplikacji** okno dialogowe, dostępna z **Publikuj** strony **projektanta projektu**.  
  
 Początkowo jest grupą pojedynczy plik o nazwie **(wymagane)**. Można tworzyć grup dodatkowych plików i przypisać im odpowiednie pliki. Nie można zmienić **grupa pobierania** dla plików, które są wymagane przez aplikację do uruchamiania. Na przykład .exe lub pliki aplikacji oznaczone jako pliki danych, trzeba należeć do **(wymagane)** grupy.  
  
 Stan publikowania domyślną wartość plik zostanie oznaczony za pomocą **(Auto)**. Na przykład .exe aplikacji ma stan publikowania **Include (Auto)** domyślnie.  
  
 Pliki z **Build Action** właściwością **zawartości** zostały oznaczone jako pliki aplikacji i zostanie oznaczony jako domyślnie włączone. Można je dołączony, wykluczony lub oznaczone jako pliki danych. Wyjątki są następujące:  
  
-   Pliki danych, takich jak SQL Database (*.mdf* i *.mdb*) plików i plików XML zostaną oznaczone jako pliki danych domyślnie.  
  
-   Odwołania do zestawów (*.dll* pliki) zostały oznaczone następujący po dodaniu odwołania: Jeśli **Kopiuj lokalnie** jest **False**, jest oznaczona domyślnie jako zestaw wymagań wstępnych (**wymagań wstępnych (Auto)**), musi znajdować się w pamięci podręcznej GAC, zanim aplikacja zostanie zainstalowana. Jeśli **Kopiuj lokalnie** jest **True**, zestaw jest oznaczony domyślnie jako zestawu aplikacji (**Include (Auto)**) i zostaną skopiowane do folderu aplikacji podczas instalacji. Odwołanie COM pojawi się w **pliki aplikacji** okno dialogowe (jako *.ocx* pliku) tylko wtedy, gdy jego **izolowany** właściwość jest ustawiona na **True**. Domyślnie zostaną dołączone.  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>Aby dodać pliki do okna dialogowego pliki aplikacji  
  
1.  Wybierz plik danych w **Eksploratora rozwiązań**.  
  
2.  W oknie Właściwości zmień **Build Action** właściwości **zawartości** wartość.  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>Aby wykluczyć pliki z publikacji technologii ClickOnce  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  Kliknij przycisk **pliki aplikacji** przycisk, aby otworzyć **pliki aplikacji** okno dialogowe.  
  
4.  W **pliki aplikacji** oknie dialogowym Wybierz plik, który chcesz wykluczyć.  
  
5.  W **stan publikowania** pól, zaznacz **wykluczyć** z listy rozwijanej.  
  
### <a name="to-mark-files-as-data-files"></a>Aby oznaczyć pliki jako pliki danych  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  Kliknij przycisk **pliki aplikacji** przycisk, aby otworzyć **pliki aplikacji** okno dialogowe.  
  
4.  W **pliki aplikacji** oknie dialogowym Wybierz plik który chcesz oznaczyć jako dane.  
  
5.  W **stan publikowania** pól, zaznacz **pliku danych** z listy rozwijanej.  
  
### <a name="to-mark-files-as-prerequisites"></a>Aby oznaczyć pliki w ramach wymagań wstępnych  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  Kliknij przycisk **pliki aplikacji** przycisk, aby otworzyć **pliki aplikacji** okno dialogowe.  
  
4.  W **pliki aplikacji** okna dialogowego Wybierz zestaw aplikacji (*.dll* pliku), którą chcesz oznaczyć jako warunek wstępny. Należy pamiętać, że aplikacja musi mieć odwołanie do zestawu aplikacji w celu pojawiają się na liście.  
  
5.  W **stan publikowania** pól, zaznacz **wymagań wstępnych** z listy rozwijanej.  
  
### <a name="to-add-a-new-file-group"></a>Aby dodać nowe grupy plików  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  Kliknij przycisk **pliki aplikacji** przycisk, aby otworzyć **pliki aplikacji** okno dialogowe.  
  
4.  W **pliki aplikacji** okno dialogowe, wybierz opcję **grupy** pola dla pliku, który chcesz dołączyć do nowej grupy.  
  
    > [!NOTE]
    >  Pliki muszą mieć **Build Action** właściwością **zawartości** przed nazwami plików są wyświetlane w **pliki aplikacji** okno dialogowe.  
  
5.  W **grupa pobierania** pól, zaznacz  **\<nowy... >** z listy rozwijanej.  
  
6.  W **Nowa grupa** okno dialogowe, wprowadź nazwę grupy, a następnie kliknij przycisk **OK**.  
  
### <a name="to-add-a-file-to-a-group"></a>Aby dodać plik do grupy  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  Kliknij przycisk **pliki aplikacji** przycisk, aby otworzyć **pliki aplikacji** okno dialogowe.  
  
4.  W **pliki aplikacji** okno dialogowe, wybierz opcję **grupy** pola dla pliku, który chcesz dołączyć do nowej grupy.  
  
5.  W **grupa pobierania** wybierz grupę z listy rozwijanej.  
  
    > [!NOTE]
    >  Nie można zmienić **grupa pobierania** dla plików, które są wymagane przez aplikację do uruchamiania.  
  
## <a name="see-also"></a>Zobacz także  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)