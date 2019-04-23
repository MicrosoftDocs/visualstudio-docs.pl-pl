---
title: Właściwości pola i interfejsy okna | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03f3c9ca624f0cccae5f9a21573fdcf01b7e9143
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060231"
---
# <a name="properties-window-fields-and-interfaces"></a>Pola i interfejsy okna właściwości
Model do wyboru ustalić, jakie informacje są wyświetlane w **właściwości** okna opiera się na okno, które ma fokus w środowisku IDE. Każdego okna, a obiekt w obrębie wybranego okna może mieć jego obiekt kontekstu wyboru wypchnięte do kontekst zaznaczenia globalnego. Środowisko aktualizuje kontekst zaznaczenia globalnych z wartościami z ramki okna, gdy to okno ma fokus. Po zmianie fokusu kończy kontekst zaznaczenia.

## <a name="tracking-selection-in-the-ide"></a>Śledzenie zaznaczenia w środowisku IDE
 Ramka okna lub lokacji należących do środowiska IDE, ma usługi o nazwie <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Poniższe kroki pokazują, jak zmiany w wyborze spowodowane przez użytkownika, zmiana fokusu do innego otwartego okna lub wybraniu elementu innego projektu w **Eksploratora rozwiązań**, zaimplementowany, aby zmienić zawartość wyświetlaną w  **Właściwości** okna.

1. Obiekt utworzony przez Twojego pakietu VSPackage, który jest zlokalizowany w wywołaniach wybrane okno <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> mieć <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> wywołania <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.

2. Kontener wyboru, dostarczone przez wybrane okno tworzy własne <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> obiektu. Gdy zostanie zmieniony na wybór pakietu VSPackage wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> o dowolnym w środowisku, w tym **właściwości** okna zmiany. Umożliwia także dostęp do informacji o hierarchii i elementów związanych z nowe zaznaczenie.

3. Wywoływanie <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> i przekazanie do niej elementy na wybraną hierarchię `VSHPROPID_BrowseObject` wypełnia parametr <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> obiektu.

4. Obiekt pochodzi od [interfejsu IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) jest zwracany w przypadku [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) dla żądanego elementu, a środowisko jest zawijany do <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (patrz następny krok). Jeśli wywołanie zakończy się niepowodzeniem, środowiska sprawia, że drugie wywołanie `IVsHierarchy::GetProperty`, podając mu kontenerze zaznaczenia [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) podać hierarchii element lub elementy.

    Projektu pakietu VSPackage nie powoduje utworzenia <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ponieważ okno dostarczane przez środowisko pakietu VSPackage, który zawiera go (na przykład **Eksploratora rozwiązań**) tworzy <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> w jej imieniu.

5. Środowisko wywołuje metody <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> można pobrać obiektów na podstawie `IDispatch` interfejsu, aby wypełnić **właściwości** okna.

   Gdy wartość w **właściwości** okno zostanie zmieniony, implementować pakietów VSPackage `IVsTrackSelectionEx::OnElementValueChangeEx` i `IVsTrackSelectionEx::OnSelectionChangeEx` do zgłoszenia tej zmiany wartości elementu. Następnie wywołuje środowisko <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> lub <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> zapewnienie informacji wyświetlanych w **właściwości** okna synchronizowane z wartości właściwości. Aby uzyskać więcej informacji, zobacz [aktualizacji wartości właściwości w oknie dialogowym właściwości](#updating-property-values-in-the-properties-window).

   Oprócz wybierając inny element projektu w **Eksploratora rozwiązań** Aby wyświetlić właściwości powiązanych z tego elementu, można także innego obiektu z okna formularza lub dokumentu za pomocą listy rozwijanej, dostępne w **Właściwości** okna. Aby uzyskać więcej informacji, zobacz [lista obiektów okna właściwości](../../extensibility/internals/properties-window-object-list.md).

   Możesz zmienić sposób wyświetlania informacji w **właściwości** siatki okna z alfabetycznym do kategorii, a jeśli to możliwe, można także otworzyć stronę właściwości dla wybranego obiektu, klikając odpowiednią przyciski na  **Właściwości** okna. Aby uzyskać więcej informacji, zobacz [przyciski okna właściwości](../../extensibility/internals/properties-window-buttons.md) i [stron właściwości](../../extensibility/internals/property-pages.md).

   Na koniec dołu **właściwości** okno zawiera również opis pola wybranego w **właściwości** siatki okna. Aby uzyskać więcej informacji, zobacz [wprowadzenie opisy pól z okna właściwości](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a> Aktualizowanie wartości właściwości w oknie dialogowym właściwości
Istnieją dwa sposoby, aby zachować **właściwości** okna zsynchronizowane ze zmian wartości właściwości. Pierwszy jest wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejs, który zapewnia dostęp do funkcji obsługi okien podstawowych, w tym dostęp do i tworzenia okna dokumentów i narzędzi, które są dostarczane przez środowisko. W poniższych krokach opisano ten proces synchronizacji.

### <a name="updating-property-values-using-ivsuishell"></a>Aktualizowanie wartości właściwości, za pomocą elementu

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Aby zaktualizować wartości właściwości, za pomocą interfejsu elementu

1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> usługi) dowolnym momencie tego pakietów VSPackage, projektów, lub edytorów muszą tworzyć lub wyliczenia narzędzia lub dokumentu.

2. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> zapewnienie **właściwości** okna zsynchronizowany ze zmianami właściwości projektu (lub innego wybranego obiektu, przeglądanie przez **właściwości** okna) bez implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> i wyzwalania <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> zdarzenia.

3. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> i wyłączyć, odpowiednio, powiadomienie klienta zdarzeń hierarchii bez konieczności hierarchii do zaimplementowania <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.

### <a name="updating-property-values-using-iconnection"></a>Aktualizowanie wartości właściwości, za pomocą elementu IConnection
 Drugim sposobem utrzymywania **właściwości** okna zsynchronizowane ze zmian wartości właściwości jest zaimplementowanie `IConnection` na składnika obiektu, aby wskazać istnienie wychodzących interfejsów. Jeśli chcesz zlokalizować nazwę właściwości, pochodzi z obiektu <xref:System.ComponentModel.ICustomTypeDescriptor>. <xref:System.ComponentModel.ICustomTypeDescriptor> Wdrożenia można modyfikować deskryptorów właściwości zwraca i Zmień nazwę właściwości. Aby zlokalizować opis, Utwórz atrybut pochodzący od <xref:System.ComponentModel.DescriptionAttribute> i zastąpić właściwość Description.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Zagadnienia dotyczące implementowania interfejsu element IConnection

1. `IConnection` zapewnia dostęp do obiektu podrzędnego modułu wyliczającego z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfejsu. Umożliwia również dostęp do wszystkich połączeń punktu podrzędnych obiektów, każdy który implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu.

2. Dowolny obiekt przeglądania jest odpowiedzialny za wdrażanie <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> zdarzeń. **Właściwości** okna poinformuję dla zdarzenia ustawione za pośrednictwem `IConnection`.

3. Punkt połączenia kontroluje liczbę połączeń (jeden lub więcej) pozwala ono jego implementacja obiektu <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Punkt połączenia, który zezwala na tylko jeden interfejs może zwracać <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> metody.

4. Klient może wywołać `IConnection` interfejs do uzyskiwania dostępu do obiektu podrzędnego modułu wyliczającego z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfejsu. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Interfejsu może być wywoływany w celu wyliczenia punkty połączenia dla każdego interfejsu wychodzącego identyfikator (IID).

5. `IConnection` również można wywołać w celu uzyskania dostępu do obiektów podrzędnych punktów połączenia za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejs dla każdego IID wychodzących. Za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu, klient rozpoczyna się lub kończy pętlę doradztwa technicznego dotyczącego z obiektu umożliwiający nawiązywanie połączeń i synchronizacją firmy klienta. Klienta można również wywołać <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu, aby uzyskać obiekt modułu wyliczającego z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interfejsu wyliczyć połączeń, które dysponuje informacjami.

## <a name="getting-field-descriptions-from-the-properties-window"></a> Wprowadzenie opisy pól z okna właściwości
W dolnej części **właściwości** , obszar opisu wyświetlane są informacje związane z pól wybranych właściwości. Ta funkcja jest włączona domyślnie. Jeśli chcesz ukryć pole opisu, kliknij prawym przyciskiem myszy **właściwości** oknie i kliknij przycisk **opis**. Ten sposób spowoduje również usunięcie znacznik wyboru obok pozycji **opis** tytuł w oknie menu. Wyświetlanie pola ponownie, wykonując te same kroki, aby przełączyć **opis** ponownie.

 Informacje w polu opisu pochodzą z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Każda metoda, interfejsu, klasa coclass i tak dalej, może mieć Niezlokalizowany `helpstring` atrybutu w bibliotece typów. **Właściwości** okna pobiera ciąg, z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.

### <a name="to-specify-localized-help-strings"></a>Aby określić parametry zlokalizowanej pomocy

1. Dodaj `helpstringdll` atrybutu po instrukcji library w bibliotece typów (`typelib`).

   > [!NOTE]
   >  Ten krok jest opcjonalny, jeśli biblioteka typów znajduje się w pliku biblioteki (.olb) obiektu.

2. Określ `helpstringcontext` atrybuty dla ciągów. Można również określić `helpstring` atrybutów.

    Te atrybuty różnią się od `helpfile` i `helpcontext` atrybuty, które znajdują się w tematach pomocy plik chm rzeczywistych.

   Można pobrać informacji o opis ma być wyświetlany nazwę właściwości wyróżnione **właściwości** wywołania okna <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> dla właściwości, która jest zaznaczone, określając żądane `lcid` atrybutu dla Ciąg wyjściowy. Wewnętrznie <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> znajdzie plik .dll, określone w `helpstringdll` atrybutu i wywołania `DLLGetDocumentation` z tym plikiem dll, przy użyciu określonego kontekstu i `lcid` atrybutu.

   Podpis i implementację `DLLGetDocumentation` są:

```cpp
STDAPI DLLGetDocumentation
(
   ITypeLib * /* ptlib */,
   ITypeInfo * /* ptinfo */,
   LCID /* lcid */,
   DWORD dwCtx,
   BSTR * pbstrHelpString
);
```

 `DLLGetDocumentation` Funkcja musi być Eksport zdefiniowany w pliku .def biblioteki dll.

 Wewnętrznie pliku olb jest tworzony, który jest faktycznie biblioteki DLL. Ta biblioteka DLL zawiera jeden zasób, typu pliku biblioteki (.tlb) i jeden eksportowanych `DLLGetDocumentation`.

 W przypadku plików .olb `helpstringdll` atrybut jest opcjonalny, ponieważ jest on tego samego pliku, który zawiera w samym pliku .tlb.

 Można pobrać ciągów do wyświetlenia na **opisy** okienko, w związku z tym, co najmniej trzeba jest określić `helpstring` atrybutu w bibliotece typów. Jeśli chcesz, aby te ciągi, które mają zostać zlokalizowane, należy określić `helpstringdll` (opcjonalne) atrybutu i `helpstringcontext` atrybut (wymagane) i zaimplementuj `DLLGetDocumentation`.

 Brak dodatkowych interfejsów, które muszą zostać zaimplementowane podczas pobierania informacji za pośrednictwem firmy idl `helpstringcontext` atrybutu i `DLLGetDocumentation`.

 Innym sposobem uzyskania zlokalizowana nazwa i opis właściwości jest implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Aby uzyskać więcej informacji dotyczących implementacja tej metody, zobacz [właściwości pola i interfejsy okna](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Zobacz także

- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)