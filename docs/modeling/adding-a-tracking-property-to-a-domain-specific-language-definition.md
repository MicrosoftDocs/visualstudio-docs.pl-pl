---
title: Dodawanie właściwości śledzenia do definicji języka specyficznego dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 21899be482e47152e8ca60d78535f49613f52ede
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53946045"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Dodawanie właściwości śledzenia do definicji języka specyficznego dla domeny

W tym instruktażu przedstawiono sposób dodawania właściwości śledzenia do modelu domeny.

A *śledzenia domeny* właściwość jest właściwością, która może być aktualizowana przez użytkownika, ale która ma wartość domyślną, która jest obliczana na podstawie wartości innych właściwości domeny lub elementów.

W narzędzia języka specyficznego dla domeny (narzędzia DSL), nazwy wyświetlanej właściwości klasy domeny ma wartość domyślną, która jest obliczana przy użyciu nazwy klasy domeny, ale użytkownik może na przykład zmień wartość w czasie projektowania lub zresetować je do obliczonej wartości.

W tym instruktażu utworzysz języka specyficznego dla domeny (DSL), który ma Namespace, właściwość, która ma wartość domyślną, w oparciu o właściwość Namespace domyślny model śledzenia. Aby uzyskać więcej informacji na temat śledzenia właściwości, zobacz [Definiowanie właściwości śledzenia](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).

- Obsługa narzędzia DSL, śledzenie deskryptorów właściwości. Jednak projektanta DSL nie można dodać właściwości śledzenia do języka. W związku z tym należy dodać niestandardowy kod definiować ani implementować właściwości śledzenia.

  Właściwości śledzenia ma dwa stany: śledzenie i zaktualizowane przez użytkownika. Śledzenie właściwości oferują następujące funkcje:

- W stanie śledzenia, obliczana jest wartość właściwości śledzenia, a wartość jest aktualizowana co inne właściwości, zmiana modelu.

- Gdy na zaktualizowanej według stanu użytkownika, wartość właściwości śledzenia zachowuje wartość, do którego użytkownik ostatnim ustawieniu właściwości.

- W **właściwości** oknie **resetowania** polecenia właściwości śledzenia jest włączone tylko, gdy właściwość jest na zaktualizowanej według stanu użytkownika. **Resetowania** polecenie ustawia parametry logowania właściwości śledzenia do śledzenia stanu.

- W **właściwości** okna, gdy właściwość śledzenia jest w stanie śledzenia, a jego wartość jest wyświetlana w regularnych czcionki.

- W **właściwości** okna, gdy właściwość śledzenia na zaktualizowanej według stanu użytkownika, jego wartość jest wyświetlany czcionką pogrubioną.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu, należy najpierw zainstalować te składniki:


| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581) |

## <a name="create-the-project"></a>Utwórz projekt

1.  Utwórz projekt projektanta języka specyficznego dla domeny. Nadaj mu nazwę `TrackingPropertyDSL`.

2.  W **Kreator projektanta języka specyficznego dla domeny**, ustaw następujące opcje:

    1.  Wybierz **MinimalLanguage** szablonu.

    2.  Użyj domyślnej nazwy dla języka specyficznego dla domeny `TrackingPropertyDSL`.

    3.  Ustaw rozszerzenie dla plików modelu do `trackingPropertyDsl`.

    4.  Ikona szablon domyślny na użytek plików modelu.

    5.  Ustaw nazwę produktu, który ma `Product Name`.

    6.  Ustaw nazwę firmy w celu `Company Name`.

    7.  Użyj wartości domyślnej głównej przestrzeni nazw dla projektów w rozwiązaniu `CompanyName.ProductName.TrackingPropertyDSL`.

    8.  Zezwalaj na kreatora, aby utworzyć plik klucza o silnej nazwie do zestawów.

    9. Przejrzyj szczegóły rozwiązania, a następnie kliknij przycisk **Zakończ** Aby utworzyć projekt definicji DSL.

## <a name="customize-the-default-dsl-definition"></a>Dostosowywanie domyślnego definicji DSL
 W tej sekcji można dostosować definicji DSL, który zawiera następujące elementy:

-   Namespace, śledzenie właściwości dla każdego elementu modelu.

-   Właściwość logiczna IsNamespaceTracking dla każdego elementu modelu. Ta właściwość będzie wskazywać, czy właściwość śledzenia jest w stanie śledzenia lub zaktualizowane według stanu użytkownika.

-   Właściwość Namespace domyślne dla modelu. Ta właściwość będzie służyć do obliczania wartości domyślnej Namespace śledzenia właściwości.

-   Właściwość CustomElements obliczana dla modelu. Ta właściwość wskazuje część elementy, które mają niestandardowej przestrzeni nazw.

### <a name="to-add-the-domain-properties"></a>Aby dodać właściwości domeny

1.  W oknie projektanta DSL, kliknij prawym przyciskiem myszy **ExampleModel** klasy domeny, wskaż **Dodaj**, a następnie kliknij przycisk **elementu DomainProperty**.

    1.  Nazwa nowej właściwości `DefaultNamespace`.

    2.  W **właściwości** okno nowej właściwości ustawione **wartości domyślnej** do `DefaultNamespace`i ustaw **typu** do **ciąg**.

2.  Aby **ExampleModel** domeny klasy, Dodaj właściwość domeny o nazwie `CustomElements`.

     W **właściwości** okno nowej właściwości ustawione **rodzaj** do **obliczona**.

3.  Aby **ExampleElement** domeny klasy, Dodaj właściwość domeny o nazwie `Namespace`.

     W **właściwości** okno nowej właściwości ustawione **jest możliwa do przeglądania** do **False**i ustaw **rodzaj** do **wartości CustomStorage** .

4.  Aby **ExampleElement** domeny klasy, Dodaj właściwość domeny o nazwie `IsNamespaceTracking`.

     W **właściwości** okno nowej właściwości ustawione **jest możliwa do przeglądania** do **False**ustaw **wartości domyślnej** do `true`i ustaw **Typu** do **logiczna**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Aktualizowanie elementów diagramu i szczegóły języka DSL

1.  W oknie projektanta DSL, kliknij prawym przyciskiem myszy **ExampleShape** kształt geometryczny, wskaż **Dodaj**, a następnie kliknij przycisk **Dekoratora tekstu**.

    1.  Nazwa nowego elementu decorator tekstu `NamespaceDecorator`.

    2.  W **właściwości** ustawić okno dla dekoratora tekstu **pozycji** do **InnerBottomLeft**.

2.  W oknie Projektant DSL wybierz linii łączącej **ExampleElement** klasy **ExampleShape** kształtu.

    1.  W **szczegóły języka DSL** wybierz **mapy Dekoratora** kartę.

    2.  W **Dekoratory** listy wybierz **NamespaceDecorator**, zaznacz jej pole wyboru, a następnie na **Właściwość wyświetlania** listy wybierz pozycję **Namespace**.

3.  W **Eksplorator DSL**, rozwiń węzeł **klasami domeny** folderu, kliknij prawym przyciskiem myszy **ExampleElement** węzłem, a następnie kliknij przycisk **Dodaj nowy deskryptor typu domeny**.

    1.  Rozwiń **ExampleElement** , a następnie wybierz węzeł **deskryptorze typu niestandardowego (deskryptor typu domeny)** węzła.

    2.  W **właściwości** okno deskryptor typu domeny, ustaw **kodowanego niestandardowe** do **True**.

4.  W **Eksplorator DSL**, wybierz opcję **zachowanie serializacji kodu Xml** węzła.

    1.  W **właściwości** oknie **niestandardowe, ładowanie publikacji** do **True**.

## <a name="transform-templates"></a>Przekształcanie szablonów

Skoro zdefiniowano klasy domeny i właściwości dla DSL, można sprawdzić, czy w definicji DSL mogą zostać przekształcone poprawnie ponownego generowania kodu dla projektu.

1.  Na **Eksploratora rozwiązań** narzędzi, kliknij przycisk **Przekształć wszystkie szablony**.

2.  System generuje kod dla rozwiązania, a następnie zapisuje DslDefinition.dsl. Aby uzyskać informacje na temat formatu XML plików definicji, zobacz [plik DslDefinition.dsl](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Twórz pliki dla niestandardowego kodu

Kiedy przekształcasz wszystkie szablony, system generuje kod źródłowy, który definiuje języka specyficznego dla domeny w projektach języka Dsl i DslPackage. Tak, aby uniknąć konfliktu z wygenerowanego tekstu, należy napisać niestandardowy kod w plikach, które różnią się od plików wygenerowanego kodu.

Należy podać kod do przechowywania wartości i stanu właściwości śledzenia. Aby ułatwić rozróżnienie niestandardowy kod z wygenerowanego kodu i uniknąć konfliktów nazw plików, należy umieścić pliki niestandardowy kod w oddzielnym podfolderze.

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DSL** projekt, wskaż opcję **Dodaj**, a następnie kliknij przycisk **nowy Folder**. Nadaj nazwę nowego folderu `CustomCode`.

2.  Kliknij prawym przyciskiem myszy nowy **atrybut CustomCode** folderu, wskaż **Dodaj**, a następnie kliknij przycisk **nowy element**.

3.  Wybierz **pliku z kodem** szablonu, ustaw **nazwa** do `NamespaceTrackingProperty.cs`, a następnie kliknij przycisk **OK**.

     Plik NamespaceTrackingProperty.cs zostanie utworzony i otwarty do edycji.

4.  W tym folderze utwórz następujące pliki kodu: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, i `TypeDescriptor.cs`.

5.  W **DslPackage** projektu, należy także utworzyć `CustomCode` folderze i Dodaj do niej `Package.cs` pliku kodu.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Dodawanie klas pomocniczych na potrzeby obsługi śledzenia właściwości

Do pliku HelperClasses.cs Dodaj `TrackingHelper` i `CriticalException` klas w następujący sposób. Będziesz odwoływać się te klasy w dalszej części tego przewodnika.

1.  Dodaj następujący kod do pliku HelperClasses.cs.

    ```csharp
    using System;
    using System.Collections;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        internal static class TrackingHelper
        {
            /// <summary>Notify each model element in a collection that a tracked
            /// property has changed.</summary>
            /// <param name="store">The store for the model.</param>
            /// <param name="collection">The collection of model elements that
            /// contain the tracking property.</param>
            /// <param name="propertyId">The ID of the tracking property.</param>
            /// <param name="trackingPropertyId">The ID of the property that
            /// indicates whether the tracking property is tracking.</param>
            internal static void UpdateTrackingCollectionProperty(
                Store store,
                IEnumerable collection,
                Guid propertyId,
                Guid trackingPropertyId)
            {
                DomainPropertyInfo propInfo =
                    store.DomainDataDirectory.GetDomainProperty(propertyId);

                DomainPropertyInfo trackingPropInfo =
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);

                Debug.Assert(propInfo != null);
                Debug.Assert(trackingPropInfo != null);
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),
                    "Tracking property not specified as a boolean");

                foreach (ModelElement element in collection)
                {
                    // If the tracking property is currently tracking, then notify
                    // it that the tracked property has changed.
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);
                    if (isTracking)
                    {
                        propInfo.NotifyValueChange(element);
                    }
                }
            }
        }

        /// <summary>Helper class to flag critical exceptions from ones that are
        /// safe to ignore.</summary>
        internal static class CriticalException
        {
            /// <summary>Gets whether an exception is critical and can not be
            /// ignored.</summary>
            /// <param name="ex">The exception to check.</param>
            /// <returns>True if the exception is critical.</returns>
            internal static bool IsCriticalException(Exception ex)
            {
                if (ex is NullReferenceException
                    || ex is StackOverflowException
                    || ex is OutOfMemoryException
                    || ex is System.Threading.ThreadAbortException)
                    return true;

                if (ex.InnerException != null)
                    return IsCriticalException(ex.InnerException);

                return false;
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Dodawanie kodu niestandardowego dla niestandardowego deskryptora typu

Implementowanie `GetCustomProperties` metodę dla deskryptora typu dla `ExampleModel` klasy domeny.

> [!NOTE]
> Kod generowany przez narzędzia języka Specyficznego dla niestandardowego deskryptora typu dla `ExampleModel` wywołania `GetCustomProperties`; jednak narzędzia DSL nie generują kodu, która implementuje metodę.

Definiowanie ta metoda tworzy śledzenia deskryptor właściwość Namespace śledzenia właściwości. Ponadto umożliwia zapewnienie atrybuty dla właściwości śledzenia **właściwości** okno, aby poprawnie wyświetlić właściwości.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Aby zmodyfikować deskryptora typu dla klasy domeny ExampleModel

1.  Dodaj następujący kod do pliku TypeDescriptor.cs.

    ```csharp
    using System;
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the custom type descriptor for the ExampleElement domain class, add
        // the GetCustomProperties method.
        public partial class ExampleElementTypeDescriptor
        {
            /// <summary>Returns the property descriptors for the described
            /// ExampleElement domain class.</summary>
            /// <remarks>This method adds the tracking property descriptor.
            /// </remarks>
            private PropertyDescriptorCollection GetCustomProperties(
                Attribute[] attributes)
            {
                // Get the default property descriptors from the base class
                PropertyDescriptorCollection propertyDescriptors =
                    base.GetProperties(attributes);

                // Get a reference to the model element that is being described.
                ExampleElement source = this.ModelElement as ExampleElement;

                //Add the descriptor for the tracking property.
                if (source != null)
                {
                    DomainPropertyInfo domainProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.NamespaceDomainPropertyId);

                    DomainPropertyInfo trackingProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);

                    // Define attributes for the tracking property so that the
                    // Properties window displays the property correctly.
                    Attribute[] attr = new Attribute[] {
                        new DisplayNameAttribute("Element Namespace"),
                        new DescriptionAttribute("The namespace of the element."),
                        new CategoryAttribute("Tracking Properties"),
                    };

                    propertyDescriptors.Add(new TrackingPropertyDescriptor(
                        source, domainProperty, trackingProperty, attr));
                }

                // Return the property descriptors for this element
                return propertyDescriptors;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-package"></a>Dodawanie kodu niestandardowego pakietu

Wygenerowany kod definiuje dostawcy opisu typu dla klasy domeny ExampleElement; Jednakże należy dodać kod, aby nakazać DSL, aby użyć tego dostawcy opisu typu.

1.  Dodaj następujący kod do pliku Package.cs.

    ```csharp
    using System.ComponentModel;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // Override the default Initialize method.
        internal sealed partial class TrackingPropertyDSLPackage
        {
            protected override void Initialize()
            {
                // Add the custom type descriptor for the ExampleElement type.
                TypeDescriptor.AddProvider(
                    new ExampleElementTypeDescriptionProvider(),
                    typeof(ExampleElement));

                base.Initialize();
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-model"></a>Dodawanie kodu niestandardowego modelu

Implementowanie `GetCustomElementsValue` metodę `ExampleModel` klasy domeny.

> [!NOTE]
> Kod generowany przez narzędzia języka Specyficznego dla `ExampleModel` wywołania `GetCustomElementsValue`; jednak narzędzia DSL nie generują kodu, która implementuje metodę.

Definiowanie `GetCustomElementsValue` metoda zapewnia logiki dla właściwości CustomElements obliczane `ExampleModel`. Ta metoda zlicza `ExampleElement` klas domeny, które mają Namespace, śledzenie właściwość, która ma wartość użytkownik zaktualizował i zwraca ciąg, który reprezentuje ta liczba jako część łączna liczba elementów w modelu.

Ponadto Dodaj `OnDefaultNamespaceChanged` metody `ExampleModel`i zastępowania `OnValueChanged` metody `DefaultNamespacePropertyHandler` zagnieżdżona klasa `ExampleModel` do wywołania `OnDefaultNamespaceChanged`.

Ponieważ właściwości DefaultNamespace jest używane do obliczania Namespace śledzenia właściwości `ExampleModel` musi powiadomić wszystkich `ExampleElement` klas domeny, których wartość właściwości DefaultNamespace została zmieniona.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Aby zmodyfikować właściwości Obsługa śledzona właściwość

1.  Dodaj następujący kod do pliku ExampleModel.cs.

    ```csharp
    using System.Linq;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        public partial class ExampleModel
        {
            public string GetCustomElementsValue()
            {
                if (this.Elements.Count == 0) return "0/0";

                int number = this.Elements.Count(e => !e.IsNamespaceTracking);
                return string.Format("{0}/{1}", number, this.Elements.Count);
            }

            #region Value changed handler for the tracked property

            // When a tracked property changes, it needs to notify all of the properties
            // that track it.

            /// <summary>Called by the DefaultNamespace property value handler when the
            /// DefaultNamespace property changes.</summary>
            /// <param name="oldValue">The previous value of the property.</param>
            /// <param name="newValue">The new value of the property.</param>
            protected virtual void OnDefaultNamespaceChanged(
                string oldValue, string newValue)
            {
                // Use the helper class to notify all of the elements in the model
                // that the default namespace has changed.
                TrackingHelper.UpdateTrackingCollectionProperty(
                    this.Store,
                    this.Elements,
                    ExampleElement.NamespaceDomainPropertyId,
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);
            }

            // Update the change handler for the DefaultNamespace property.
            internal sealed partial class DefaultNamespacePropertyHandler
            {
                /// <summary>Called when the DefaultNamespace property changes.</summary>
                /// <param name="element">The model element that has the property that
                /// changed.</param>
                /// <param name="oldValue">The previous value of the property.</param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleModel element, string oldValue, string newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);

                    if (!element.Store.InUndoRedoOrRollback)
                    {
                        element.OnDefaultNamespaceChanged(oldValue, newValue);
                    }
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-for-the-tracking-property"></a>Dodawanie kodu niestandardowego dla właściwości śledzenia

Dodaj `CalculateNamespace` metody `ExampleElement` klasy domeny.

Definiowanie tej metody zawiera logikę dla właściwości CustomElements obliczane `ExampleModel`. Ta metoda zlicza `ExampleElement` klas domeny, które mają Namespace, śledzenie właściwość, która znajduje się w zaktualizowane według stanu użytkownika i zwraca ciąg, który reprezentuje ta liczba jako część łączna liczba elementów w modelu.

Ponadto Dodaj magazyn i metody get i set dla właściwości magazynu niestandardowego Namespace `ExampleElement` klasy domeny.

> [!NOTE]
> Kod, który Generowanie narzędzia DSL `ExampleModel` wywołuje get i ustawianie metody; jednak narzędzia DSL nie generują kod, który implementuje metody.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Aby dodać metodę dla deskryptora typu niestandardowego

1.  Dodaj następujący kod do pliku NamespaceTrackingProperty.cs.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the domain class that has the tracking property, add the caluclation
        // for when the property is tracking.
        public partial class ExampleElement
        {
            /// <summary>Calculates the actual value of the property when it is
            /// tracking.</summary>
            /// <returns>The value of the tracking property when it is
            /// tracking.</returns>
            /// <remarks>Making this method virtual allows child classes to modify
            /// the calculation. This method does not need to perform validation, as
            /// its caller handles validation prior to calling this method.
            /// <para>In this case, the tracking value depends on the default namespace
            /// property of the parent model.</para></remarks>
            protected virtual string CalculateNamespace()
            {
                return this.ExampleModel.DefaultNamespace;
            }

            #region Tracking property implementation

            // Implement the Namespace domain property of the ExampleElement domain class,
            // and update the IsNamespaceTracking domain property value handler.

            /// <summary>Storage for the Namespace property.</summary>
            private string namespaceStorage;

            /// <summary>Gets the value of the Namespace property.</summary>
            /// <returns>The value of the Namespace property.</returns>
            private string GetNamespaceValue()
            {
                // Only retrieve the tracked value if the store is not in the
                // middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!loading && this.IsNamespaceTracking)
                {
                    try
                    {
                        return this.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                        return default(string);
                    }
                    catch (Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                        else
                        {
                            return default(string);
                        }
                    }
                }

                return namespaceStorage;
            }

            /// <summary>Sets the value of the Namespace property.</summary>
            /// <param name="value">The new value for the property.</param>
            private void SetNamespaceValue(string value)
            {
                namespaceStorage = value;

                // Only update the state of the tracking property if the store is
                // not in the middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!this.Store.InUndoRedoOrRollback && !loading)
                {
                    this.IsNamespaceTracking = false;
                }
            }

            // Update the default behavior of the ExampleElement.IsNamespaceTracking
            // domain property value handler.
            internal sealed partial class IsNamespaceTrackingPropertyHandler
            {
                /// <summary>Called after the IsNamespaceTracking property changes.
                /// </summary>
                /// <param name="element">The model element that has the property
                /// that changed.</param>
                /// <param name="oldValue">The previous value of the property.
                /// </param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleElement element, Boolean oldValue, Boolean newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);
                    if (!element.Store.InUndoRedoOrRollback && newValue)
                    {
                        DomainPropertyInfo propInfo =
                            element.Store.DomainDataDirectory.GetDomainProperty(
                                ExampleElement.NamespaceDomainPropertyId);
                        propInfo.NotifyValueChange(element);
                    }
                }

                /// <summary>Performs the reset operation for the IsNamespaceTracking
                /// property for a model element.</summary>
                /// <param name="element">The model element that has the property
                /// to reset.</param>
                internal void ResetValue(ExampleElement element)
                {
                    object calculatedValue = null;

                    try
                    {
                        calculatedValue = element.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                    }
                    catch (System.Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                    }

                    if ((calculatedValue != null
                        && object.Equals(element.Namespace, calculatedValue)))
                    {
                        element.isNamespaceTrackingPropertyStorage = true;
                    }
                }

                /// <summary>Method to set IsNamespaceTracking to false so that this
                /// instance of this tracking property is not storage-based.
                /// </summary>
                /// <param name="element">The element on which to reset the property
                /// value.</param>
                internal void PreResetValue(ExampleElement element)
                {
                    // Force the IsNamespaceTracking property to false so that the value
                    // of the Namespace property is retrieved from storage.
                    element.isNamespaceTrackingPropertyStorage = false;
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-to-support-serialization"></a>Dodawanie kodu niestandardowego, aby obsługiwać serializacji

Dodaj kod do obsługi niestandardowe zachowanie po załadowaniu do serializacji XML.

> [!NOTE]
> Kod, że narzędzia DSL generować wywołania `OnPostLoadModel` i `OnPostLoadModelAndDiagram` metod; jednak narzędzia DSL nie generują kod, który implementuje te metody.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Aby dodać kod do obsługi niestandardowe zachowanie po załadowaniu

1.  Dodaj następujący kod do pliku Serialization.cs.

    ```csharp
    using System;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        #region Helper classes for maintaining state while the store is serializing.

        public abstract partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Reset the tracking state properties to their natural values
            /// based on comparing storage with calculation.</summary>
            /// <param name="store">The store that contains this model.</param>
            internal static void ResetTrackingProperties(Store store)
            {
                // Two passes required - one to set all elements to storage-based
                // then another to set some back to being tracking.
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.PreResetIsTrackingProperties();
                        continue;
                    }
                }
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.ResetIsTrackingProperties();
                        continue;
                    }
                }
            }
        }

        // Add the pre-reset and reset methods for the model element.
        public partial class ExampleElement
        {
            /// <summary>Calls the pre-reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void PreResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);
            }

            /// <summary>Calls the reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void ResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);
            }
        }

        #endregion

        #region Custom serialization code

        // To the serialization helper for the TrackingPropertyDSL class, add post
        // load handlers to bind the tracking property to the serialization process.
        // These handlers manage the tracking states and property values when the
        // model is serialized and deserialized.
        public partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Customize model loading.</summary>
            /// <param name="serializationResult">The serialization result from the
            /// load operation.</param>
            /// <param name="partition">The partition in which the new
            /// instance was created.</param>
            /// <param name="fileName">The name of the file from which the
            /// instance was deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.
            /// </param>
            private void OnPostLoadModel(
                SerializationResult serializationResult,
                Partition partition,
                string fileName,
                ExampleModel modelRoot)
            {
            }

            /// <summary>Customize model and diagram loading.</summary>
            /// <param name="serializationResult">Stores serialization result from
            /// the load operation.</param>
            /// <param name="modelPartition">Partition in which the new
            /// instance will be created.</param>
            /// <param name="modelFileName">Name of the file from which the
            /// instance will be deserialized.</param>
            /// <param name="diagramPartition">Partition in which the new
            /// diagram instance will be created.</param>
            /// <param name="diagramFileName">Name of the file from which the
            /// diagram instance will be deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.</param>
            /// <param name="diagram">The diagram matching the modelRoot.</param>
            private void OnPostLoadModelAndDiagram(
                SerializationResult serializationResult,
                Partition modelPartition,
                string modelFileName,
                Partition diagramPartition,
                string diagramFileName,
                ExampleModel modelRoot,
                TrackingPropertyDSLDiagram diagram)
            {
                Debug.Assert(modelPartition != null);
                Debug.Assert(modelPartition.Store != null);

                // Tracking properties need to be set up according to whether the
                // serialization matches the calculated values.
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(
                    modelPartition.Store);
            }
        }

        #endregion
    }
    ```

## <a name="test-the-language"></a>Testowanie języka

Następnym krokiem jest, aby skompilować i uruchomić projektanta DSL w nowe wystąpienie klasy [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] tak, aby sprawdzić, czy właściwości śledzenia działa poprawnie.

1. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

2. Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.

    Eksperymentalne kompilacji [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] otwiera **debugowanie** rozwiązania, które zawiera plik pusty test.

3. W **Eksploratora rozwiązań**, kliknij dwukrotnie plik Test.trackingPropertyDsl, aby otworzyć go w projektancie, a następnie kliknij na powierzchnię projektową.

    Należy zauważyć, że w **właściwości** okna diagramu, **domyślne Namespace** właściwość jest **DefaultNamespace**i **elementy niestandardowe** właściwość **0/0**.

4. Przeciągnij **ExampleElement** elementu z **przybornika** na powierzchni diagramu.

5. W **właściwości** okna dla elementu, wybierz opcję **Element Namespace** właściwości i zmień wartość z **DefaultNamespace** do  **OtherNamespace**.

    Należy zauważyć, że wartość **Element Namespace** są teraz wyświetlane pogrubioną czcionką.

6. W **właściwości** okna, kliknij prawym przyciskiem myszy **Element Namespace**, a następnie kliknij przycisk **resetowania**.

    Wartość właściwości jest zmieniana na **DefaultNamespace**, a wartość jest przedstawiana w regularnych czcionki.

    Kliknij prawym przyciskiem myszy **Element Namespace** ponownie. **Resetowania** polecenie teraz jest wyłączone, ponieważ właściwość jest obecnie w stanie śledzenia.

7. Przeciągnij kolejny **ExampleElement** z **przybornika** na powierzchni diagramu, a następnie zmień jego **Element Namespace** do **OtherNamespace**.

8. Kliknij przycisk powierzchni projektowej.

    W **właściwości** okna dla diagramu, a wartość **elementy niestandardowe** jest teraz **1/2**.

9. Zmiana **domyślne Namespace** dla diagramu z **DefaultNamespace** do **NewNamespace**.

     **Namespace** pierwszy ścieżki elementu **domyślne Namespace** właściwości, natomiast **Namespace** drugiego elementu zachowuje swoją wartość użytkownikzaktualizował **OtherNamespace**.

10. Zapisywanie rozwiązania, a następnie zamknij eksperymentalne kompilacji.

## <a name="next-steps"></a>Następne kroki

Jeśli planujesz użyć właściwości więcej niż jeden śledzenia lub zaimplementować właściwości śledzenia w więcej niż jednym języku DSL, można utworzyć szablon tekstowy w celu wygenerowania wspólny kod do obsługi poszczególnych właściwości śledzenia. Aby uzyskać więcej informacji na temat szablonów tekstowych, zobacz [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Instrukcje: Tworzenie rozwiązania języka dotyczącego określonej domeny](../modeling/how-to-create-a-domain-specific-language-solution.md)
