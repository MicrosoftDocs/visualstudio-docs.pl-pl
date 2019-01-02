---
title: Opcje konfiguracji — Przegląd | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ed12330a2acce09a5fb8a9aabc3b434b4c42fd8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956013"
---
# <a name="configuration-options-overview"></a>Omówienie opcji konfiguracji
Projekty w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] może obsługiwać wiele konfiguracji, które może być kompilowana, debugowania, wykonywania i/lub wdrożone. Konfiguracja jest opisane nazwany zestaw właściwości, zwykle przełączniki kompilatora i lokalizacje plików typu kompilacji. Domyślnie nowe rozwiązania zawiera dwie konfiguracje *debugowania* i *wersji*. Te konfiguracje mogą być stosowane przy użyciu ustawień domyślnych lub zmodyfikowane w celu spełnienia określonych wymagań rozwiązania lub projektu. Niektóre pakiety można tworzyć na dwa sposoby: jako edytora ActiveX lub jako składnik w miejscu. Projekty nie trzeba jednak obsługuje wiele konfiguracji. Jeśli jest dostępna tylko w jednej konfiguracji, że konfiguracja jest mapowany do wszystkich konfiguracji rozwiązania.  
  
 Konfiguracje zwykle składają się z dwóch części: Nazwa konfiguracji (takich jak *debugowania* lub *wersji*) i ustawienia platformy. Nazwa platformy konfiguracji identyfikuje środowisko, które elementy docelowe konfiguracji, takich jak interfejs API zestawu lub platformy systemu operacyjnego. Użytkownicy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie można utworzyć platformy; musi wybrać z opcji projektu pakietu VSPackage umożliwia. Podczas instalacji przez użytkownika pakietu VSPackage, platforma dostarczania utworzonych podczas opracowywania aplikacji pakietu może pojawiać się w dowolnej nazwy platformy desired na podstawie wszystkich kryteriów ustawione przez autora pakietu. Użytkownik może następnie wybrać z listy platform udostępniane się za pomocą pakietu VSPackage, gdy są tworzone na stronach właściwości.  
  
 Nazw platform są opcjonalne, ponieważ nie wszystkie projekty obsługuje koncepcji platform. Podczas konfiguracji brakuje nazwy platformy, ciąg **n/d** jest wyświetlana w interfejsie użytkownika.  
  
 Każde rozwiązanie ma swój własny zestaw konfiguracji, tylko jeden z nich może być aktywne w danym momencie. Konfiguracja rozwiązania to zbiór nie więcej niż jedną konfigurację z każdego projektu. Jest ustalenie "nie więcej niż" ze względu na możliwość wykluczanie projektów z konfiguracji rozwiązania. Użytkownicy mogą tworzyć własne konfiguracje niestandardowe rozwiązanie.  
  
 W poniższej tabeli przedstawiono typowe konfiguracje ustawień projektu. Wiersze są oznaczone etykietami z nazwami konfiguracji i kolumny z nazwami platformy.  
  
|Nazwa konfiguracji|Platforma: Win32|Platforma: Win64|  
|------------------------|----------------------|----------------------|  
|*Debugowanie*|\<Ustawienia systemu Win32 debugowania >|\<Ustawienia Win64 debugowania >|  
|*Wersja*|\<Ustawienia systemu Win32 wydania >|\<Ustawienia Win64 wydania >|  
|*MyConfig*|Brak|\<Ustawienia MyConfig Win64 >|  
  
> [!NOTE]
>  Nie można utworzyć *MyConfig* konfiguracji rozwiązania, który nie obejmuje platformy Win32, chyba, że celem projektu nie obsługuje systemu Win32.  
  
 Zmiana aktywnej konfiguracji rozwiązania wybiera zestaw konfiguracje projektu, które jest wbudowane, uruchamiania, debugowania lub wdrożone w ramach tego rozwiązania. Na przykład, jeśli zmienisz konfigurację aktywngo rozwiązania z *wersji* do *debugowania*, wszystkie projekty w ramach tego rozwiązania są automatycznie tworzone za pomocą konfiguracji projektów w Konfiguracja debugowania rozwiązania. Konfiguracje projektów są również nazywane *debugowania* , chyba że użytkownik wprowadził ręczne zmiany w środowisku programu Configuration Manager.  
  
 Właściwości konfiguracji rozwiązania, które są przechowywane dla każdego projektu obejmują nazwę projektu, nazwa konfiguracji projektu, flagi, aby wskazać, czy do tworzenia lub wdrażania i nazwa platformy. Aby uzyskać więcej informacji, zobacz [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md).  
  
 Użytkownik może wyświetlić i ustaw parametry konfiguracji rozwiązania, wybierając rozwiązania w hierarchii (Eksplorator rozwiązań) i otwieranie stron właściwości. Podobnie można wyświetlić i ustawić parametry konfiguracji projektu, wybierając projekt w Eksploratorze rozwiązań i otwieranie stron właściwości dla tego projektu.  
  
 Użytkownika można także utworzyć jeden projekt przy użyciu ustawienia konfiguracji wydania i wszystkie pozostałe z ustawienia konfiguracji debugowania, jeśli to konieczne. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md).  
  
 Na poniższym diagramie przedstawiono, jak są implementowane interfejsy, które obsługują konfiguracje rozwiązania i projektu:  
  
 ![Ilustracja dotycząca konfiguracji interfejsów](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfejsy konfiguracji  
  
 Kilka uwagi odnoszące się do poprzedniego diagramu:  
  
- `IDispatch` jest oznaczone jako opcjonalne w obiekt konfiguracji. Ściślej mówiąc jest to opcjonalne mieć interfejsy konfiguracji w obiekcie przeglądania.  
  
- `IVsDebuggableProjectCfg` oznaczone jako opcjonalne w obiekt konfiguracji, ale jest wymagany do obsługi debugowania.  
  
- `IVsProjectCfg2` oznaczone jako opcjonalne w obiekt konfiguracji, ale wymagane jest grupowanie pomocy technicznej w danych wyjściowych.  
  
- Obiekt dostawcy konfiguracji jest oznaczony jako obiekt opcjonalny, ale ta opcja jest miejsce, do jej wdrożenia. Obiekt może wdrożyć na obiekt projektu lub na oddzielnym obiektem.  
  
- `IVsCfgProvider2` jest potrzebny do obsługi platformy i konfiguracji do edycji. `IVsCfgProvider` jest wystarczająca, jeśli nie należy implementować te funkcje.  
  
- Niektóre z tych obiektów, które przedstawiono na diagramie jako oddzielne obiekty mogą być połączone w tej samej klasy, gdzie jest to praktyczne zgodnie z wymaganiami określonego projektu. W innych tematach w tej sekcji jednak obiekty i interfejsy skojarzone z tymi obiektami zostanie dokładnie omówione zgodnie z scenariusz przedstawiony na diagramie.  
  
- Określone obiekty są implementowane oddzielnie. Na przykład projektu i tworzenia rozwiązań są dokonywane na oddzielnych wątkach i obiekt na potrzeby zarządzania życie kompilację oddzielnie od obiektu opisujący konfigurację kompilacji.  
  
  Aby uzyskać więcej informacji na temat interfejsów obiektów konfiguracji i interfejsów obiektów dostawcy konfiguracji na poprzednim rysunku, zobacz [obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md). Ponadto [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md) zamieszczono więcej informacji dotyczących zależności i konstruktora kompilacji konfiguracji interfejsów obiektów i [konfiguracji projektu do zarządzania wdrożeniem](../../extensibility/internals/project-configuration-for-managing-deployment.md) dalsze informacje interfejsów, dołączonych do narzędzia konfiguracji wdrażania i wdrożenie zależności obiektów. Na koniec [konfiguracji projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md) opisano grupy danych wyjściowych i interfejsów obiektów danych wyjściowych i użycie stron właściwości do wyświetlania i ustaw właściwości konfiguracji-zależnych od ustawień lokalnych.  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)