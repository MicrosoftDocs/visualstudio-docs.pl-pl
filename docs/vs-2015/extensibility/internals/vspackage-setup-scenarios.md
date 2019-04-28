---
title: Scenariusze instalacji pakietu VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58b4350812900bc11e8aaa3222b3b0898db19e13
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440789"
---
# <a name="vspackage-setup-scenarios"></a>Scenariusze instalacji pakietu VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Należy zaprojektować swój Instalatora pakietu VSPackage, aby zapewnić elastyczność. Na przykład może być konieczne w przyszłości wersji poprawki zabezpieczeń lub mogą ulec zmianie strategii biznesowej, która wymaga dokładnego side-by-side obsługą kontroli wersji.  
  
 W [obsługi wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), możesz przeczytać o korzyści i problemy dotyczące obsługi instalacje side-by-side [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] z udostępnionego lub side-by-side instalacje Twojego pakietu VSPackage. Krótko mówiąc, pakietów VSPackage side-by-side zapewniają większą elastyczność do obsługi nowych funkcji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Scenariusze omówione w tym temacie nie są tylko wybrane opcje, ale są przedstawione jako sugerowane najlepsze rozwiązanie.  
  
## <a name="components-privacy-and-sharing"></a>Składniki, ochrony prywatności i udostępnianie  
  
##### <a name="make-your-components-independent"></a>Uniezależnić składników  
 Po identyfikować i wypełnić składnika, przypisać `GUID`i wdrożyć składnik, nie można zmienić jego skład. Jeśli zmienisz kompozycji składnika, wynikowy składnika musi być nowego składnika z nową `GUID`. Biorąc pod uwagę następujące fakty, największą elastyczność versioning jest udzielone, wprowadzając jednostki niezależne, samodzielnego każdego składnika. Aby uzyskać więcej informacji na temat zasad regulujących składniki zobacz [zmiany kodu składnika](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) i [co się stanie, jeśli składnik reguły są uszkodzone?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Nie należy mieszać prywatnych i udostępnionych zasobów w składniku  
 Zliczanie odwołań występuje na poziomie składnika. W związku z tym mieszanie zasobów udostępnionych i prywatnych w jednym składniku uniemożliwia aktualizują zasoby z prywatnych, takich jak plik wykonywalny bez zastępowania także zasoby udostępnione. W tym scenariuszu tworzy problemy ze zgodnością wsteczną i uniemożliwia tworzenie funkcji side-by-side.  
  
 Na przykład, wartości rejestru są używane do rejestrowania swojej pakietów VSPackage przy użyciu [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] powinny być oddzielone w składniku z jednego używane do rejestrowania swojej pakietów VSPackage przy użyciu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Wartości rejestru lub plików udostępnionych przejść w jeszcze inny składnik.  
  
## <a name="scenario-1-shared-vspackage"></a>Scenariusz 1: Shared VSPackage  
 W tym scenariuszu udostępnionego pakietu VSPackage (pojedynczy plik binarny, który obsługuje wiele wersji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]) jest dostarczany w pakiecie Instalatora Windows. Rejestrowanie z każdą wersją programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest kontrolowany przy użyciu funkcji wybierane przez użytkownika. Oznacza to również, że po przypisaniu do oddzielania funkcji, każdego składnika można wybrać indywidualnie celu instalacji lub odinstalowania, zapewnieniem użytkownikowi kontroli nad integrowanie pakietu VSPackage różne wersje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. (Zobacz [funkcje Instalatora Windows](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) Aby uzyskać więcej informacji na temat korzystania z funkcji w pakietów Instalatora Windows.)  
  
 ![VS Shared VSPackage graphic](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
Udostępnione Instalatora pakietu VSPackage  
  
 Jak pokazano na ilustracji, składników udostępnionych stają się częścią funkcji Feat_Common, która będzie zawsze instalowana. Przez funkcje Feat_VS2002 i Feat_VS2003 widoczności, użytkownicy mogą wybrać w momencie instalacji w wersjach programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mają pakietu VSPackage, aby zintegrować. Użytkownicy mogą także skorzystać z trybu konserwacji Instalatora Windows, dodawanie i usuwanie funkcji, która w tym przypadku dodaje lub usuwa informacje o rejestracji pakietu VSPackage z różnych wersji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
> [!NOTE]
> Ustawienie funkcji kolumnę wyświetlaną na wartość 0 powoduje ukrycie go. Wartość w kolumnie poziom niski, taką jak 1, gwarantuje, że zawsze zostanie ona zainstalowana. Aby uzyskać więcej informacji, zobacz [właściwość INSTALLLEVEL](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) i [tabeli funkcji](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Scenariusz 2: Udostępnione aktualizacji pakietu VSPackage  
 W tym scenariuszu jest dostarczany zaktualizowaną wersję Instalatora pakietu VSPackage w scenariuszu 1. Rozważań aktualizacja dodaje obsługę [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], ale mogą być również prostsze zabezpieczeń poprawki lub poprawka błędu dodatku service pack. Instalowanie składników nowszej zasady Instalatora Windows wymagają, że niezmienione składniki już w systemie nie są ponownie kopiowane. W takim przypadku system w wersji 1.0 już istnieje zastąpić aktualizowanego składnika Comp_MyVSPackage.dll i Pozwól użytkownikom wybrać, można dodać nowej funkcji Feat_VS2005 za jego pomocą Comp_VS2005_Reg składnika.  
  
> [!CAUTION]
> Zawsze, gdy pakietu VSPackage jest współużytkowana przez wiele wersji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], istotne jest, że kolejne wersje pakietu VSPackage zachowania zgodności z poprzednimi wersjami z wcześniejszych wersji programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. W przypadku, gdy nie można zachować zgodności z poprzednimi wersjami, należy użyć pakietów VSPackage side-by-side przypadku wartość prywatna. Aby uzyskać więcej informacji, zobacz [obsługi wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![VS Shared VS Package Update Image](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Udostępnione Instalatora aktualizacji pakietu VSPackage  
  
 W tym scenariuszu przedstawiono nowego Instalatora pakietu VSPackage, korzystając z zalet Instalatora Windows obsługę niewielkie uaktualnienia. Użytkownicy instalują wersji 1.1 i uaktualni ona w wersji 1.0. Jednak nie jest konieczne w wersji 1.0 w systemie. Tym samym Instalator zainstaluje wersji 1.1 w systemie bez wersji 1.0. Zaletą zapewnienie niewielkie uaktualnienia w ten sposób jest to, że nie jest konieczne przechodzą przez prac związanych z tworzeniem uaktualnienia Instalatora i Instalator pełnego produktu. Jeden Instalator wykonuje oba zadania. Poprawkę zabezpieczeń lub service pack może zamiast tego skorzystaj z zalet poprawek Instalatora Windows. Aby uzyskać więcej informacji, zobacz [stosowanie poprawek i uaktualnień](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Scenariusz 3: Side-by-Side pakietu VSPackage  
 W tym scenariuszu przedstawiono dwa pliki instalacyjne pakietu VSPackage — jeden dla każdej wersji programu Visual Studio .NET 2003 i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Każdy Instalator instaluje side-by-side i prywatnych, pakietu VSPackage (taki, który jest specjalnie utworzone i zainstalowane dla konkretnej wersji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]). Każdego pakietu VSPackage znajduje się w jego własnej składnika. W związku z tym, każdy może być indywidualnie obsługiwany przy użyciu poprawek lub obsługi wersji. Ponieważ biblioteki DLL pakietu VSPackage teraz jest specyficzny dla wersji, jest bezpieczne dołączyć swoje informacje rejestracyjne w jednym składniku jako biblioteki DLL.  
  
 ![Po stronie VS&#45;przez&#45;grafiki pakietu programu VS po stronie](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Instalator pakietu VSPackage Side-by-side  
  
 Instalator, każdy zawiera również kod, który jest współużytkowana przez dwa pliki instalacyjne. Po zainstalowaniu udostępnionego kodu do wspólnej lokalizacji instalacji oba pliki .msi zostanie zainstalowany kod udostępniony tylko raz. Instalator w drugi po prostu zwiększa licznik odwołań do składnika. Licznik odwołań temu, jeśli jeden z pakietów VSPackage zostanie odinstalowany, kod udostępniony pozostanie dla pakietu VSPackage. Drugi pakietu VSPackage odinstalowanie spowoduje także udostępnionego kodu zostaną usunięte.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Scenariusz 4: Side-by-Side pakietu VSPackage aktualizacji  
 W tym scenariuszu Twojego pakietu VSPackage dla [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] poniesione przez usługę security luk w zabezpieczeniach, jeśli jest konieczne do wysyłania aktualizacji. Tak jak w scenariuszu 2 można utworzyć nowy plik msi, która aktualizuje istniejącą instalację do poprawkę zabezpieczeń, a także wdrażanie nowych instalacji poprawki zabezpieczeń już w miejscu.  
  
 W tym przypadku pakietu VSPackage jest zarządzanych pakietu VSPackage, zainstalowane w globalnej pamięci podręcznej zestawów (GAC). Kiedy ponownie kompilujesz hurtownię go, aby uwzględniał poprawki zabezpieczeń, należy zmienić numer poprawki część numeru wersji zestawu. Informacje o rejestracji dla nowego numeru wersji zestawu zastępuje poprzednią wersję, powodując [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] można załadować zestawu stały.  
  
 ![Po stronie VS&#45;przez&#45;grafiki VS pakietu aktualizacji](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Instalator aktualizacji pakietu VSPackage Side-by-side  
  
 **Uwaga** Aby uzyskać więcej informacji na temat wdrażania zestawów side-by-side, zobacz [upraszczanie wdrażania i rozwiązywania piekłem bibliotek DLL, przy użyciu programu .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [Instalator Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Obsługiwanie wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
