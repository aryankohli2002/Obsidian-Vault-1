[Python SQLAlchemy model with dynamic table name - EasyDevGuide.com](https://www.easydevguide.com/posts/dynamic_table)

class CustomerTable(Base):

    __abstract__ = True

    passwordid = Column(Integer, primary_key=True, autoincrement=True)

    website = Column(String(100), nullable=False)

    username = Column(String(50), nullable=False)

    password = Column(String(100), nullable=False)

  

def get_customer_table_name(name):  

    tablename = 'password_table_for_user_%s' % name  # dynamic table name

    class_name = 'CustomerTable'

    Model = type(class_name, (CustomerTable,), {

        '__tablename__': tablename

    })

    return Model

  

def add_password_for_apps():

    user = 'aryankohli2002'

    #user = session['username']

    CustomerTable = get_customer_table_name(user)

    website = 'your_website.com'

    username_on_website = 'your_username'

    password = 'your_secure_password'

    new_record = CustomerTable(website, username_on_website, password)

    sess.add(new_record)

    sess.commit()

  

add_password_for_apps()

  

def create_custom_table():

    usr = session['username']

    class CustomTable(Base):

        __tablename__ = f"password_table_for_user_{usr}"

  

        passwordid = Column(Integer, primary_key=True, autoincrement=True)

        website = Column(String(100), nullable=False)

        username = Column(String(50), nullable=False)

        password = Column(String(100), nullable=False)

  

    Base.metadata.create_all(engine, tables=[CustomTable.__table__])