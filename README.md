# silverstripe-codegen

codegen (pick up name from Generators) args

e.g

    codegen DataObject FilterType ...

    would call new DataObjectGenerator()->generate('FilterType', ...);


    Generator
        - name e.g DataObject,
        - shorthand  e.g do

    GeneratorExtension
        - update for extensions
        e.g
        FormGeneratorExtension->updateFormAttributes()
    
// automatically register

    DataObject generator
        - $db stub
        - $has_one stub
        - $has_many stub
        - $defaults stub
        - canCreate,canEdit,canDelete,canView stubs
        - getCMSForm() *after the $db,$has_one,$has_many has been updated
        - sortOrder with remove from CMSForm && onBeforeWrite
    
    Page generator
        - $db stub
        - $has_one stub
        - $has_many stub
        - $defaults stub
        - getCMSForm() *after the $db,$has_one,$has_many has been updated

    Form Class generator
        - validation using html5, parsley
        - parsley attributes e.g (setAttribute('parsley-validate' && 'novalidate'))
        - bootstrap classes
        - optionally send email
        - creates fields based on data object attributes + action for submit
        - Ajax support?

    Form HTML generator
        - bootstrap grid container

    ModelAdmin generator
        - typical 
        - ? do you want to include getList()
        - ? do you want to include sortable rows
        
    ApiController generator
        - create methods
        - default url
        - add route to routes.yml
        
    SinglePageAdmin
        - takes a page and creates a single page admin 
        - sort order
    
    RestfulApiController generator
        - takes a dataobject and creates restful actions
    
    could generate based on .yml config file, generate dataobject, form html, api, getCMSFields() etc
    
    DataObject
        - Product:
            db:
                firstName:
                    type: string
                    class: form-control
                    required: true
                    attributes:
                    
    
    add CMSAction since its a pain in the us
                    


    Spec files
    
    Objects
        - Product
            fields:
                Title: Text,required,unique(),50%,.form-control,sameAs(EmailAddress)
                EmailAddress: Email
                
    Generator:
        DataObject(Product)
        DataObjectForm(Product)
        DataObjectFormHTML(Product)
        
    DataObject: Product,Type2,Type3 etc
    Form: Product,Type1,Type2 etc
