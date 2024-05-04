import java.util.*;
class Gmail
{
	static Scanner sc = new Scanner(System.in);
	private String GmailId = "project@gmail.com";
	String getmailid()
	{
		return GmailId;
	}
	static int display(int otp)
	{
		System.out.println("   otp :  "+otp);
		return otp;
	}
}	
class examination extends Gmail
{
	
	private String uid = sc.next();
	private String password = sc.next();
	void setuid(String uid)
	{
		this.uid = uid;
	}
	void setpassword(String password)
import java.util.*;
class Gmail
{
	static Scanner sc = new Scanner(System.in);
	private String GmailId = "project@gmail.com";
	String getmailid()
	{
		return GmailId;
	}
	static int display(int otp)
	{
		System.out.println("   otp :  "+otp);
		return otp;
	}
}	
class examination extends Gmail
{
	
	private String uid = sc.next();
	private String password = sc.next();
	void setuid(String uid)
	{
		this.uid = uid;
	}
	void setpassword(String password)
	{
		this.password = password;
	}
	String getuid()
	{
		return uid;
	}
	String getpassword()
	{
		return password;
	}
}
class user extends examination
{
	static Random r = new Random();
	static user obj ;
	static void sigin()
	{
		System.out.println("    enter userid : ");
		String id = sc.next();
		System.out.println("    enter password  : ");
		String password = sc.next();
		if(id.equals(obj.getuid()) && password.equals(obj.getpassword()))
		{
			System.out.println("		Login Success		");
			start();
			
		}
		else if(!id.equals(obj.getuid()) && password.equals(obj.getpassword()))
		{
			validateid();
		}
		else if(id.equals(obj.getuid()) && !password.equals(obj.getpassword()))
		{
			validatepassword();
		}
	}
	static void validateid()
	{
		int i;
		for( i = 1;i<3;i++)
		{
			System.out.println("     invalid userid  please renter the id     ");
			String id = sc.next();
			if(id.equals(obj.getuid()))
			{
				System.out.println("		Login success		");
				start();
				break;
			}			
		}
		if(i>=3)
		{
			System.out.println("      your login has reached the limit     ");
			System.out.println("      do you want to reset the id           ");
			String b = sc.next();
			if(b.equalsIgnoreCase("yes"))
			{
				System.out.println("       Enter your registerd mail id    ");
				String mailid = sc.next();
				if(mailid.equals(obj.getmailid()))
				{
					otp();
				}
				else
				{
					end();
				}
			}
			else
			{
				end();
			}
		}
	}
	static void validatepassword()
	{
		int i;
		for( i = 1;i<3;i++)
		{
			System.out.println("     invalid password please renter the paasword     ");
			String pwsd = sc.next();
			if(pwsd.equals(obj.getpassword()))
			{
				System.out.println("	Login success	");
				start();
				break;
			}			
		}
		if(i>=3)
		{
			System.out.println("      your login has reached the limit     ");
			System.out.println("      do you want to reset the pasword           ");
			String b = sc.next();
			if(b.equalsIgnoreCase("yes"))
			{
				System.out.println("       Enter your registerd mail id    ");
				String mailid = sc.next();
				if(mailid.equals(obj.getmailid()))
				{
					otp();
				}
				else
				{
					end();
				}
			}
			else
			{
				end();
			}
		}

	}
	static void otp()
	{
		System.out.println("    otp has sent to your registerd mail id	");
			int k = r.nextInt(8999)+1000;
			int otp = display(k);
			check (k);
	}
	static void check(int otp)
	{
		if(otp==sc.nextInt())
		{
			System.out.println("	What do you want change?	");
			String opt=sc.next();
			if(opt.equalsIgnoreCase("id"))
			{
				System.out.println("    enter new userid      ");
				String id = sc.next();
				obj.setuid(id);
				System.out.println("    id updated successfullyy    ");
				System.out.println("	do you want to sigin ");
				sigin();
			}
			else if(opt.equalsIgnoreCase("password"))
			{
				System.out.println("    enter new password      ");
				String pwsd = sc.next();
				obj.setpassword(pwsd);
				System.out.println("    password updated successfullyy    ");
				System.out.println("	do you want to sigin ");
				sigin();
			}
		}
		else
		{
			System.out.print("	you entered wrong otp	");
			System.out.print("	Resend otp	");
			String s=sc.next();
			if(s.equalsIgnoreCase("yes"))
			otp();
			else
			end();
		}
	}
	static void login()
	{	
		System.out.println("       Enter userid and password to create acc");	
		obj = new user();
		System.out.println("       Registraion is successfull  ");
		System.out.println("       do you  want to sigin    ");
		String b = sc.next();
		if(b.equalsIgnoreCase("yes"))
		{
			sigin();
		}
		else
		{
			end();
		}	
	}
	static void start()
	{
       
		System.out.println("	Do you want to start the exam	");
		String s=sc.next();
		if(s.equalsIgnoreCase("yes"))
		{
        		Exam exam = new Exam();
			exam.addQuestion("MS-Word is an example of_____ \n1. An operating system\n2. A processing device\n3. Application software\n4. An input device\n ", 0, 3);
	 	exam.addQuestion("Ctrl, Shift and Alt are called____ keys. \n1. modifier \n2. function \n3. alphanumeric\n4. adjustment\n ",1, 1);
        	exam.addQuestion("National Income estimates in India are prepared by__\n1. Reserve Bank of India\n2. Central statistical organisation\n3.  Planning Commission\n4. Indian statistical Institute\n ",2, 2);
        	exam.addQuestion("Fathometer is used to measure_\n1. Earthquakes\n2. Rainfall\n3. Ocean depth\n4. Sound intensity\n ", 3,3);
       			exam.conductExam();
			end();
		}
		else
		{
			end();
		}
		
	}
	static void end()
	{
                String green="\u001B[32m";
               System.out.print(green);
		System.out.println("		Thank you		");
                String reset="\u001B[0m";
               System.out.print(reset);
               
               
	}
}
class Exam 
{
	private String  questions[];
    	private int answer[];
    	private int userAnswer[];
    	public Exam() 
	{
        	questions = new String[4];
		answer=new int[4];
		userAnswer=new int[4];
    	}
    	public void addQuestion(String question,int qnum,int ans) 
	{
		questions[qnum]=question;
		answer[qnum]=ans; 
    	}
    	public void conductExam() 
	{
        	int score = 0;
        	Scanner sc = new Scanner(System.in);
        	System.out.println("	Your Exam has been Started	");
		int c=0;
        	for (int i = 0; i < questions.length; i++) 
		{		
            		System.out.println("\nQuestion " +( i + 1 )+ ": " + questions[i] );
            		System.out.print("Your answer: ");
           		userAnswer[i] = sc.nextInt();
			if (userAnswer[i]==(answer[i])) 
			{
                		score++;
			}
        	}
        	System.out.println("		Exam finished!		");
		if(score==questions.length)
		{
			String yellow="\u001B[33m";
			String blink="\u001B[5m";
			String reset="\u001B[0m";
			System.out.print(yellow);
			System.out.println(blink);
			System.out.println("		congratulations		");
			System.out.println(reset);
		}
		for(int i=0;i<questions.length;i++)
		{
			System.out.println("Q "+(i+1)+" "+" \n actual answer # " +answer[i]+ " \n your Answer #"+ userAnswer[i]);
		}

        		System.out.println("Your score: " + score + " out of " + questions.length);
    	}
}
class Main extends user
{
	public static void main(String[] args) 
	{
                String blue = "\u001B[34m";
                String purple="\u001B[35m";
                String green="\u001B[32m";
                String blink="\u001B[5m";
                String reset="\u001B[0m";
                String yellow="\u001B[33m";
                String red ="\u001B[31m";
                System.out.print(red);
                System.out.println("          ****************************	");
                System.out.print(blue);
                System.out.println(blink);
                System.out.print("            Welcome to the Online Exam!	");
                System.out.println(reset);
                System.out.println(red);
                System.out.print("           ****************************	");
                System.out.println(reset);
		login();
    	}
}import java.util.*;
class Gmail
{
	static Scanner sc = new Scanner(System.in);
	private String GmailId = "project@gmail.com";
	String getmailid()
	{
		return GmailId;
	}
	static int display(int otp)
	{
		System.out.println("   otp :  "+otp);
		return otp;
	}
}	
class examination extends Gmail
{
	
	private String uid = sc.next();
	private String password = sc.next();
	void setuid(String uid)
	{
		this.uid = uid;
	}
	void setpassword(String password)
	{
		this.password = password;
	}
	String getuid()
	{
		return uid;
	}
	String getpassword()
	{
		return password;
	}
}
class user extends examination
{
	static Random r = new Random();
	static user obj ;
	static void sigin()
	{
		System.out.println("    enter userid : ");
		String id = sc.next();
		System.out.println("    enter password  : ");
		String password = sc.next();
		if(id.equals(obj.getuid()) && password.equals(obj.getpassword()))
		{
			System.out.println("		Login Success		");
			start();
			
		}
		else if(!id.equals(obj.getuid()) && password.equals(obj.getpassword()))
		{
			validateid();
		}
		else if(id.equals(obj.getuid()) && !password.equals(obj.getpassword()))
		{
			validatepassword();
		}
	}
	static void validateid()
	{
		int i;
		for( i = 1;i<3;i++)
		{
			System.out.println("     invalid userid  please renter the id     ");
			String id = sc.next();
			if(id.equals(obj.getuid()))
			{
				System.out.println("		Login success		");
				start();
				break;
			}			
		}
		if(i>=3)
		{
			System.out.println("      your login has reached the limit     ");
			System.out.println("      do you want to reset the id           ");
			String b = sc.next();
			if(b.equalsIgnoreCase("yes"))
			{
				System.out.println("       Enter your registerd mail id    ");
				String mailid = sc.next();
				if(mailid.equals(obj.getmailid()))
				{
					otp();
				}
				else
				{
					end();
				}
			}
			else
			{
				end();
			}
		}
	}
	static void validatepassword()
	{
		int i;
		for( i = 1;i<3;i++)
		{
			System.out.println("     invalid password please renter the paasword     ");
			String pwsd = sc.next();
			if(pwsd.equals(obj.getpassword()))
			{
				System.out.println("	Login success	");
				start();
				break;
			}			
		}
		if(i>=3)
		{
			System.out.println("      your login has reached the limit     ");
			System.out.println("      do you want to reset the pasword           ");
			String b = sc.next();
			if(b.equalsIgnoreCase("yes"))
			{
				System.out.println("       Enter your registerd mail id    ");
				String mailid = sc.next();
				if(mailid.equals(obj.getmailid()))
				{
					otp();
				}
				else
				{
					end();
				}
			}
			else
			{
				end();
			}
		}

	}
	static void otp()
	{
		System.out.println("    otp has sent to your registerd mail id	");
			int k = r.nextInt(8999)+1000;
			int otp = display(k);
			check (k);
	}
	static void check(int otp)
	{
		if(otp==sc.nextInt())
		{
			System.out.println("	What do you want change?	");
			String opt=sc.next();
			if(opt.equalsIgnoreCase("id"))
			{
				System.out.println("    enter new userid      ");
				String id = sc.next();
				obj.setuid(id);
				System.out.println("    id updated successfullyy    ");
				System.out.println("	do you want to sigin ");
				sigin();
			}
			else if(opt.equalsIgnoreCase("password"))
			{
				System.out.println("    enter new password      ");
				String pwsd = sc.next();
				obj.setpassword(pwsd);
				System.out.println("    password updated successfullyy    ");
				System.out.println("	do you want to sigin ");
				sigin();
			}
		}
		else
		{
			System.out.print("	you entered wrong otp	");
			System.out.print("	Resend otp	");
			String s=sc.next();
			if(s.equalsIgnoreCase("yes"))
			otp();
			else
			end();
		}
	}
	static void login()
	{	
		System.out.println("       Enter userid and password to create acc");	
		obj = new user();
		System.out.println("       Registraion is successfull  ");
		System.out.println("       do you  want to sigin    ");
		String b = sc.next();
		if(b.equalsIgnoreCase("yes"))
		{
			sigin();
		}
		else
		{
			end();
		}	
	}
	static void start()
	{
       
		System.out.println("	Do you want to start the exam	");
		String s=sc.next();
		if(s.equalsIgnoreCase("yes"))
		{
        		Exam exam = new Exam();
			exam.addQuestion("MS-Word is an example of_____ \n1. An operating system\n2. A processing device\n3. Application software\n4. An input device\n ", 0, 3);
	 	exam.addQuestion("Ctrl, Shift and Alt are called____ keys. \n1. modifier \n2. function \n3. alphanumeric\n4. adjustment\n ",1, 1);
        	exam.addQuestion("National Income estimates in India are prepared by__\n1. Reserve Bank of India\n2. Central statistical organisation\n3.  Planning Commission\n4. Indian statistical Institute\n ",2, 2);
        	exam.addQuestion("Fathometer is used to measure_\n1. Earthquakes\n2. Rainfall\n3. Ocean depth\n4. Sound intensity\n ", 3,3);
       			exam.conductExam();
			end();
		}
		else
		{
			end();
		}
		
	}
	static void end()
	{
                String green="\u001B[32m";
               System.out.print(green);
		System.out.println("		Thank you		");
                String reset="\u001B[0m";
               System.out.print(reset);
               
               
	}
}
class Exam 
{
	private String  questions[];
    	private int answer[];
    	private int userAnswer[];
    	public Exam() 
	{
        	questions = new String[4];
		answer=new int[4];
		userAnswer=new int[4];
    	}
    	public void addQuestion(String question,int qnum,int ans) 
	{
		questions[qnum]=question;
		answer[qnum]=ans; 
    	}
    	public void conductExam() 
	{
        	int score = 0;
        	Scanner sc = new Scanner(System.in);
        	System.out.println("	Your Exam has been Started	");
		int c=0;
        	for (int i = 0; i < questions.length; i++) 
		{		
            		System.out.println("\nQuestion " +( i + 1 )+ ": " + questions[i] );
            		System.out.print("Your answer: ");
           		userAnswer[i] = sc.nextInt();
			if (userAnswer[i]==(answer[i])) 
			{
                		score++;
			}
        	}
        	System.out.println("		Exam finished!		");
		if(score==questions.length)
		{
			String yellow="\u001B[33m";
			String blink="\u001B[5m";
			String reset="\u001B[0m";
			System.out.print(yellow);
			System.out.println(blink);
			System.out.println("		congratulations		");
			System.out.println(reset);
		}
		for(int i=0;i<questions.length;i++)
		{
			System.out.println("Q "+(i+1)+" "+" \n actual answer # " +answer[i]+ " \n your Answer #"+ userAnswer[i]);
		}

        		System.out.println("Your score: " + score + " out of " + questions.length);
    	}
}
class Main extends user
{
	public static void main(String[] args) 
	{
                String blue = "\u001B[34m";
                String purple="\u001B[35m";
                String green="\u001B[32m";
                String blink="\u001B[5m";
                String reset="\u001B[0m";
                String yellow="\u001B[33m";
                String red ="\u001B[31m";
                System.out.print(red);
                System.out.println("          ****************************	");
                System.out.print(blue);
                System.out.println(blink);
                System.out.print("            Welcome to the Online Exam!	");
                System.out.println(reset);
                System.out.println(red);
                System.out.print("           ****************************	");
                System.out.println(reset);
		login();
    	}
}import java.util.*;
class Gmail
{
	static Scanner sc = new Scanner(System.in);
	private String GmailId = "project@gmail.com";
	String getmailid()
	{
		return GmailId;
	}
	static int display(int otp)
	{
		System.out.println("   otp :  "+otp);
		return otp;
	}
}	
class examination extends Gmail
{
	
	private String uid = sc.next();
	private String password = sc.next();
	void setuid(String uid)
	{
		this.uid = uid;
	}
	void setpassword(String password)
	{
		this.password = password;
	}
	String getuid()
	{
		return uid;
	}
	String getpassword()
	{
		return password;
	}
}
class user extends examination
{
	static Random r = new Random();
	static user obj ;
	static void sigin()
	{
		System.out.println("    enter userid : ");
		String id = sc.next();
		System.out.println("    enter password  : ");
		String password = sc.next();
		if(id.equals(obj.getuid()) && password.equals(obj.getpassword()))
		{
			System.out.println("		Login Success		");
			start();
			
		}
		else if(!id.equals(obj.getuid()) && password.equals(obj.getpassword()))
		{
			validateid();
		}
		else if(id.equals(obj.getuid()) && !password.equals(obj.getpassword()))
		{
			validatepassword();
		}
	}
	static void validateid()
	{
		int i;
		for( i = 1;i<3;i++)
		{
			System.out.println("     invalid userid  please renter the id     ");
			String id = sc.next();
			if(id.equals(obj.getuid()))
			{
				System.out.println("		Login success		");
				start();
				break;
			}			
		}
		if(i>=3)
		{
			System.out.println("      your login has reached the limit     ");
			System.out.println("      do you want to reset the id           ");
			String b = sc.next();
			if(b.equalsIgnoreCase("yes"))
			{
				System.out.println("       Enter your registerd mail id    ");
				String mailid = sc.next();
				if(mailid.equals(obj.getmailid()))
				{
					otp();
				}
				else
				{
					end();
				}
			}
			else
			{
				end();
			}
		}
	}
	static void validatepassword()
	{
		int i;
		for( i = 1;i<3;i++)
		{
			System.out.println("     invalid password please renter the paasword     ");
			String pwsd = sc.next();
			if(pwsd.equals(obj.getpassword()))
			{
				System.out.println("	Login success	");
				start();
				break;
			}			
		}
		if(i>=3)
		{
			System.out.println("      your login has reached the limit     ");
			System.out.println("      do you want to reset the pasword           ");
			String b = sc.next();
			if(b.equalsIgnoreCase("yes"))
			{
				System.out.println("       Enter your registerd mail id    ");
				String mailid = sc.next();
				if(mailid.equals(obj.getmailid()))
				{
					otp();
				}
				else
				{
					end();
				}
			}
			else
			{
				end();
			}
		}

	}
	static void otp()
	{
		System.out.println("    otp has sent to your registerd mail id	");
			int k = r.nextInt(8999)+1000;
			int otp = display(k);
			check (k);
	}
	static void check(int otp)
	{
		if(otp==sc.nextInt())
		{
			System.out.println("	What do you want change?	");
			String opt=sc.next();
			if(opt.equalsIgnoreCase("id"))
			{
				System.out.println("    enter new userid      ");
				String id = sc.next();
				obj.setuid(id);
				System.out.println("    id updated successfullyy    ");
				System.out.println("	do you want to sigin ");
				sigin();
			}
			else if(opt.equalsIgnoreCase("password"))
			{
				System.out.println("    enter new password      ");
				String pwsd = sc.next();
				obj.setpassword(pwsd);
				System.out.println("    password updated successfullyy    ");
				System.out.println("	do you want to sigin ");
				sigin();
			}
		}
		else
		{
			System.out.print("	you entered wrong otp	");
			System.out.print("	Resend otp	");
			String s=sc.next();
			if(s.equalsIgnoreCase("yes"))
			otp();
			else
			end();
		}
	}
	static void login()
	{	
		System.out.println("       Enter userid and password to create acc");	
		obj = new user();
		System.out.println("       Registraion is successfull  ");
		System.out.println("       do you  want to sigin    ");
		String b = sc.next();
		if(b.equalsIgnoreCase("yes"))
		{
			sigin();
		}
		else
		{
			end();
		}	
	}
	static void start()
	{
       
		System.out.println("	Do you want to start the exam	");
		String s=sc.next();
		if(s.equalsIgnoreCase("yes"))
		{
        		Exam exam = new Exam();
			exam.addQuestion("MS-Word is an example of_____ \n1. An operating system\n2. A processing device\n3. Application software\n4. An input device\n ", 0, 3);
	 	exam.addQuestion("Ctrl, Shift and Alt are called____ keys. \n1. modifier \n2. function \n3. alphanumeric\n4. adjustment\n ",1, 1);
        	exam.addQuestion("National Income estimates in India are prepared by__\n1. Reserve Bank of India\n2. Central statistical organisation\n3.  Planning Commission\n4. Indian statistical Institute\n ",2, 2);
        	exam.addQuestion("Fathometer is used to measure_\n1. Earthquakes\n2. Rainfall\n3. Ocean depth\n4. Sound intensity\n ", 3,3);
       			exam.conductExam();
			end();
		}
		else
		{
			end();
		}
		
	}
	static void end()
	{
                String green="\u001B[32m";
               System.out.print(green);
		System.out.println("		Thank you		");
                String reset="\u001B[0m";
               System.out.print(reset);
               
               
	}
}
class Exam 
{
	private String  questions[];
    	private int answer[];
    	private int userAnswer[];
    	public Exam() 
	{
        	questions = new String[4];
		answer=new int[4];
		userAnswer=new int[4];
    	}
    	public void addQuestion(String question,int qnum,int ans) 
	{
		questions[qnum]=question;
		answer[qnum]=ans; 
    	}
    	public void conductExam() 
	{
        	int score = 0;
        	Scanner sc = new Scanner(System.in);
        	System.out.println("	Your Exam has been Started	");
		int c=0;
        	for (int i = 0; i < questions.length; i++) 
		{		
            		System.out.println("\nQuestion " +( i + 1 )+ ": " + questions[i] );
            		System.out.print("Your answer: ");
           		userAnswer[i] = sc.nextInt();
			if (userAnswer[i]==(answer[i])) 
			{
                		score++;
			}
        	}
        	System.out.println("		Exam finished!		");
		if(score==questions.length)
		{
			String yellow="\u001B[33m";
			String blink="\u001B[5m";
			String reset="\u001B[0m";
			System.out.print(yellow);
			System.out.println(blink);
			System.out.println("		congratulations		");
			System.out.println(reset);
		}
		for(int i=0;i<questions.length;i++)
		{
			System.out.println("Q "+(i+1)+" "+" \n actual answer # " +answer[i]+ " \n your Answer #"+ userAnswer[i]);
		}

        		System.out.println("Your score: " + score + " out of " + questions.length);
    	}
}
class Main extends user
{
	public static void main(String[] args) 
	{
                String blue = "\u001B[34m";
                String purple="\u001B[35m";
                String green="\u001B[32m";
                String blink="\u001B[5m";
                String reset="\u001B[0m";
                String yellow="\u001B[33m";
                String red ="\u001B[31m";
                System.out.print(red);
                System.out.println("          ****************************	");
                System.out.print(blue);
                System.out.println(blink);
                System.out.print("            Welcome to the Online Exam!	");
                System.out.println(reset);
                System.out.println(red);
                System.out.print("           ****************************	");
                System.out.println(reset);
		login();
    	}
}import java.util.*;
class Gmail
{
	static Scanner sc = new Scanner(System.in);
	private String GmailId = "project@gmail.com";
	String getmailid()
	{
		return GmailId;
	}
	static int display(int otp)
	{
		System.out.println("   otp :  "+otp);
		return otp;
	}
}	
class examination extends Gmail
{
	
	private String uid = sc.next();
	private String password = sc.next();
	void setuid(String uid)
	{
		this.uid = uid;
	}
	void setpassword(String password)
	{
		this.password = password;
	}
	String getuid()
	{
		return uid;
	}
	String getpassword()
	{
		return password;
	}
}
class user extends examination
{
	static Random r = new Random();
	static user obj ;
	static void sigin()
	{
		System.out.println("    enter userid : ");
		String id = sc.next();
		System.out.println("    enter password  : ");
		String password = sc.next();
		if(id.equals(obj.getuid()) && password.equals(obj.getpassword()))
		{
			System.out.println("		Login Success		");
			start();
			
		}
		else if(!id.equals(obj.getuid()) && password.equals(obj.getpassword()))
		{
			validateid();
		}
		else if(id.equals(obj.getuid()) && !password.equals(obj.getpassword()))
		{
			validatepassword();
		}
	}
	static void validateid()
	{
		int i;
		for( i = 1;i<3;i++)
		{
			System.out.println("     invalid userid  please renter the id     ");
			String id = sc.next();
			if(id.equals(obj.getuid()))
			{
				System.out.println("		Login success		");
				start();
				break;
			}			
		}
		if(i>=3)
		{
			System.out.println("      your login has reached the limit     ");
			System.out.println("      do you want to reset the id           ");
			String b = sc.next();
			if(b.equalsIgnoreCase("yes"))
			{
				System.out.println("       Enter your registerd mail id    ");
				String mailid = sc.next();
				if(mailid.equals(obj.getmailid()))
				{
					otp();
				}
				else
				{
					end();
				}
			}
			else
			{
				end();
			}
		}
	}
	static void validatepassword()
	{
		int i;
		for( i = 1;i<3;i++)
		{
			System.out.println("     invalid password please renter the paasword     ");
			String pwsd = sc.next();
			if(pwsd.equals(obj.getpassword()))
			{
				System.out.println("	Login success	");
				start();
				break;
			}			
		}
		if(i>=3)
		{
			System.out.println("      your login has reached the limit     ");
			System.out.println("      do you want to reset the pasword           ");
			String b = sc.next();
			if(b.equalsIgnoreCase("yes"))
			{
				System.out.println("       Enter your registerd mail id    ");
				String mailid = sc.next();
				if(mailid.equals(obj.getmailid()))
				{
					otp();
				}
				else
				{
					end();
				}
			}
			else
			{
				end();
			}
		}

	}
	static void otp()
	{
		System.out.println("    otp has sent to your registerd mail id	");
			int k = r.nextInt(8999)+1000;
			int otp = display(k);
			check (k);
	}
	static void check(int otp)
	{
		if(otp==sc.nextInt())
		{
			System.out.println("	What do you want change?	");
			String opt=sc.next();
			if(opt.equalsIgnoreCase("id"))
			{
				System.out.println("    enter new userid      ");
				String id = sc.next();
				obj.setuid(id);
				System.out.println("    id updated successfullyy    ");
				System.out.println("	do you want to sigin ");
				sigin();
			}
			else if(opt.equalsIgnoreCase("password"))
			{
				System.out.println("    enter new password      ");
				String pwsd = sc.next();
				obj.setpassword(pwsd);
				System.out.println("    password updated successfullyy    ");
				System.out.println("	do you want to sigin ");
				sigin();
			}
		}
		else
		{
			System.out.print("	you entered wrong otp	");
			System.out.print("	Resend otp	");
			String s=sc.next();
			if(s.equalsIgnoreCase("yes"))
			otp();
			else
			end();
		}
	}
	static void login()
	{	
		System.out.println("       Enter userid and password to create acc");	
		obj = new user();
		System.out.println("       Registraion is successfull  ");
		System.out.println("       do you  want to sigin    ");
		String b = sc.next();
		if(b.equalsIgnoreCase("yes"))
		{
			sigin();
		}
		else
		{
			end();
		}	
	}
	static void start()
	{
       
		System.out.println("	Do you want to start the exam	");
		String s=sc.next();
		if(s.equalsIgnoreCase("yes"))
		{
        		Exam exam = new Exam();
			exam.addQuestion("MS-Word is an example of_____ \n1. An operating system\n2. A processing device\n3. Application software\n4. An input device\n ", 0, 3);
	 	exam.addQuestion("Ctrl, Shift and Alt are called____ keys. \n1. modifier \n2. function \n3. alphanumeric\n4. adjustment\n ",1, 1);
        	exam.addQuestion("National Income estimates in India are prepared by__\n1. Reserve Bank of India\n2. Central statistical organisation\n3.  Planning Commission\n4. Indian statistical Institute\n ",2, 2);
        	exam.addQuestion("Fathometer is used to measure_\n1. Earthquakes\n2. Rainfall\n3. Ocean depth\n4. Sound intensity\n ", 3,3);
       			exam.conductExam();
			end();
		}
		else
		{
			end();
		}
		
	}
	static void end()
	{
                String green="\u001B[32m";
               System.out.print(green);
		System.out.println("		Thank you		");
                String reset="\u001B[0m";
               System.out.print(reset);
               
               
	}
}
class Exam 
{
	private String  questions[];
    	private int answer[];
    	private int userAnswer[];
    	public Exam() 
	{
        	questions = new String[4];
		answer=new int[4];
		userAnswer=new int[4];
    	}
    	public void addQuestion(String question,int qnum,int ans) 
	{
		questions[qnum]=question;
		answer[qnum]=ans; 
    	}
    	public void conductExam() 
	{
        	int score = 0;
        	Scanner sc = new Scanner(System.in);
        	System.out.println("	Your Exam has been Started	");
		int c=0;
        	for (int i = 0; i < questions.length; i++) 
		{		
            		System.out.println("\nQuestion " +( i + 1 )+ ": " + questions[i] );
            		System.out.print("Your answer: ");
           		userAnswer[i] = sc.nextInt();
			if (userAnswer[i]==(answer[i])) 
			{
                		score++;
			}
        	}
        	System.out.println("		Exam finished!		");
		if(score==questions.length)
		{
			String yellow="\u001B[33m";
			String blink="\u001B[5m";
			String reset="\u001B[0m";
			System.out.print(yellow);
			System.out.println(blink);
			System.out.println("		congratulations		");
			System.out.println(reset);
		}
		for(int i=0;i<questions.length;i++)
		{
			System.out.println("Q "+(i+1)+" "+" \n actual answer # " +answer[i]+ " \n your Answer #"+ userAnswer[i]);
		}

        		System.out.println("Your score: " + score + " out of " + questions.length);
    	}
}
class Main extends user
{
	public static void main(String[] args) 
	{
                String blue = "\u001B[34m";
                String purple="\u001B[35m";
                String green="\u001B[32m";
                String blink="\u001B[5m";
                String reset="\u001B[0m";
                String yellow="\u001B[33m";
                String red ="\u001B[31m";
                System.out.print(red);
                System.out.println("          ****************************	");
                System.out.print(blue);
                System.out.println(blink);
                System.out.print("            Welcome to the Online Exam!	");
                System.out.println(reset);
                System.out.println(red);
                System.out.print("           ****************************	");
                System.out.println(reset);
		login();
    	}
}import java.util.*;
class Gmail
{
	static Scanner sc = new Scanner(System.in);
	private String GmailId = "project@gmail.com";
	String getmailid()
	{
		return GmailId;
	}
	static int display(int otp)
	{
		System.out.println("   otp :  "+otp);
		return otp;
	}
}	
class examination extends Gmail
{
	
	private String uid = sc.next();
	private String password = sc.next();
	void setuid(String uid)
	{
		this.uid = uid;
	}
	void setpassword(String password)
	{
		this.password = password;
	}
	String getuid()
	{
		return uid;
	}
	String getpassword()
	{
		return password;
	}
}
class user extends examination
{
	static Random r = new Random();
	static user obj ;
	static void sigin()
	{
		System.out.println("    enter userid : ");
		String id = sc.next();
		System.out.println("    enter password  : ");
		String password = sc.next();
		if(id.equals(obj.getuid()) && password.equals(obj.getpassword()))
		{
			System.out.println("		Login Success		");
			start();
			
		}
		else if(!id.equals(obj.getuid()) && password.equals(obj.getpassword()))
		{
			validateid();
		}
		else if(id.equals(obj.getuid()) && !password.equals(obj.getpassword()))
		{
			validatepassword();
		}
	}
	static void validateid()
	{
		int i;
		for( i = 1;i<3;i++)
		{
			System.out.println("     invalid userid  please renter the id     ");
			String id = sc.next();
			if(id.equals(obj.getuid()))
			{
				System.out.println("		Login success		");
				start();
				break;
			}			
		}
		if(i>=3)
		{
			System.out.println("      your login has reached the limit     ");
			System.out.println("      do you want to reset the id           ");
			String b = sc.next();
			if(b.equalsIgnoreCase("yes"))
			{
				System.out.println("       Enter your registerd mail id    ");
				String mailid = sc.next();
				if(mailid.equals(obj.getmailid()))
				{
					otp();
				}
				else
				{
					end();
				}
			}
			else
			{
				end();
			}
		}
	}
	static void validatepassword()
	{
		int i;
		for( i = 1;i<3;i++)
		{
			System.out.println("     invalid password please renter the paasword     ");
			String pwsd = sc.next();
			if(pwsd.equals(obj.getpassword()))
			{
				System.out.println("	Login success	");
				start();
				break;
			}			
		}
		if(i>=3)
		{
			System.out.println("      your login has reached the limit     ");
			System.out.println("      do you want to reset the pasword           ");
			String b = sc.next();
			if(b.equalsIgnoreCase("yes"))
			{
				System.out.println("       Enter your registerd mail id    ");
				String mailid = sc.next();
				if(mailid.equals(obj.getmailid()))
				{
					otp();
				}
				else
				{
					end();
				}
			}
			else
			{
				end();
			}
		}

	}
	static void otp()
	{
		System.out.println("    otp has sent to your registerd mail id	");
			int k = r.nextInt(8999)+1000;
			int otp = display(k);
			check (k);
	}
	static void check(int otp)
	{
		if(otp==sc.nextInt())
		{
			System.out.println("	What do you want change?	");
			String opt=sc.next();
			if(opt.equalsIgnoreCase("id"))
			{
				System.out.println("    enter new userid      ");
				String id = sc.next();
				obj.setuid(id);
				System.out.println("    id updated successfullyy    ");
				System.out.println("	do you want to sigin ");
				sigin();
			}
			else if(opt.equalsIgnoreCase("password"))
			{
				System.out.println("    enter new password      ");
				String pwsd = sc.next();
				obj.setpassword(pwsd);
				System.out.println("    password updated successfullyy    ");
				System.out.println("	do you want to sigin ");
				sigin();
			}
		}
		else
		{
			System.out.print("	you entered wrong otp	");
			System.out.print("	Resend otp	");
			String s=sc.next();
			if(s.equalsIgnoreCase("yes"))
			otp();
			else
			end();
		}
	}
	static void login()
	{	
		System.out.println("       Enter userid and password to create acc");	
		obj = new user();
		System.out.println("       Registraion is successfull  ");
		System.out.println("       do you  want to sigin    ");
		String b = sc.next();
		if(b.equalsIgnoreCase("yes"))
		{
			sigin();
		}
		else
		{
			end();
		}	
	}
	static void start()
	{
       
		System.out.println("	Do you want to start the exam	");
		String s=sc.next();
		if(s.equalsIgnoreCase("yes"))
		{
        		Exam exam = new Exam();
			exam.addQuestion("MS-Word is an example of_____ \n1. An operating system\n2. A processing device\n3. Application software\n4. An input device\n ", 0, 3);
	 	exam.addQuestion("Ctrl, Shift and Alt are called____ keys. \n1. modifier \n2. function \n3. alphanumeric\n4. adjustment\n ",1, 1);
        	exam.addQuestion("National Income estimates in India are prepared by__\n1. Reserve Bank of India\n2. Central statistical organisation\n3.  Planning Commission\n4. Indian statistical Institute\n ",2, 2);
        	exam.addQuestion("Fathometer is used to measure_\n1. Earthquakes\n2. Rainfall\n3. Ocean depth\n4. Sound intensity\n ", 3,3);
       			exam.conductExam();
			end();
		}
		else
		{
			end();
		}
		
	}
	static void end()
	{
                String green="\u001B[32m";
               System.out.print(green);
		System.out.println("		Thank you		");
                String reset="\u001B[0m";
               System.out.print(reset);
               
               
	}
}
class Exam 
{
	private String  questions[];
    	private int answer[];
    	private int userAnswer[];
    	public Exam() 
	{
        	questions = new String[4];
		answer=new int[4];
		userAnswer=new int[4];
    	}
    	public void addQuestion(String question,int qnum,int ans) 
	{
		questions[qnum]=question;
		answer[qnum]=ans; 
    	}
    	public void conductExam() 
	{
        	int score = 0;
        	Scanner sc = new Scanner(System.in);
        	System.out.println("	Your Exam has been Started	");
		int c=0;
        	for (int i = 0; i < questions.length; i++) 
		{		
            		System.out.println("\nQuestion " +( i + 1 )+ ": " + questions[i] );
            		System.out.print("Your answer: ");
           		userAnswer[i] = sc.nextInt();
			if (userAnswer[i]==(answer[i])) 
			{
                		score++;
			}
        	}
        	System.out.println("		Exam finished!		");
		if(score==questions.length)
		{
			String yellow="\u001B[33m";
			String blink="\u001B[5m";
			String reset="\u001B[0m";
			System.out.print(yellow);
			System.out.println(blink);
			System.out.println("		congratulations		");
			System.out.println(reset);
		}
		for(int i=0;i<questions.length;i++)
		{
			System.out.println("Q "+(i+1)+" "+" \n actual answer # " +answer[i]+ " \n your Answer #"+ userAnswer[i]);
		}

        		System.out.println("Your score: " + score + " out of " + questions.length);
    	}
}
class Main extends user
{
	public static void main(String[] args) 
	{
                String blue = "\u001B[34m";
                String purple="\u001B[35m";
                String green="\u001B[32m";
                String blink="\u001B[5m";
                String reset="\u001B[0m";
                String yellow="\u001B[33m";
                String red ="\u001B[31m";
                System.out.print(red);
                System.out.println("          ****************************	");
                System.out.print(blue);
                System.out.println(blink);
                System.out.print("            Welcome to the Online Exam!	");
                System.out.println(reset);
                System.out.println(red);
                System.out.print("           ****************************	");
                System.out.println(reset);
		login();
    	}
}	{
		this.password = password;
	}
	String getuid()
	{
		return uid;
	}
	String getpassword()
	{
		return password;
	}
}
class user extends examination
{
	static Random r = new Random();
	static user obj ;
	static void sigin()
	{
		System.out.println("    enter userid : ");
		String id = sc.next();
		System.out.println("    enter password  : ");
		String password = sc.next();
		if(id.equals(obj.getuid()) && password.equals(obj.getpassword()))
		{
			System.out.println("		Login Success		");
			start();
			
		}
		else if(!id.equals(obj.getuid()) && password.equals(obj.getpassword()))
		{
			validateid();
		}
		else if(id.equals(obj.getuid()) && !password.equals(obj.getpassword()))
		{
			validatepassword();
		}
	}
	static void validateid()
	{
		int i;
		for( i = 1;i<3;i++)
		{
			System.out.println("     invalid userid  please renter the id     ");
			String id = sc.next();
			if(id.equals(obj.getuid()))
			{
				System.out.println("		Login success		");
				start();
				break;
			}			
		}
		if(i>=3)
		{
			System.out.println("      your login has reached the limit     ");
			System.out.println("      do you want to reset the id           ");
			String b = sc.next();
			if(b.equalsIgnoreCase("yes"))
			{
				System.out.println("       Enter your registerd mail id    ");
				String mailid = sc.next();
				if(mailid.equals(obj.getmailid()))
				{
					otp();
				}
				else
				{
					end();
				}
			}
			else
			{
				end();
			}
		}
	}
	static void validatepassword()
	{
		int i;
		for( i = 1;i<3;i++)
		{
			System.out.println("     invalid password please renter the paasword     ");
			String pwsd = sc.next();
			if(pwsd.equals(obj.getpassword()))
			{
				System.out.println("	Login success	");
				start();
				break;
			}			
		}
		if(i>=3)
		{
			System.out.println("      your login has reached the limit     ");
			System.out.println("      do you want to reset the pasword           ");
			String b = sc.next();
			if(b.equalsIgnoreCase("yes"))
			{
				System.out.println("       Enter your registerd mail id    ");
				String mailid = sc.next();
				if(mailid.equals(obj.getmailid()))
				{
					otp();
				}
				else
				{
					end();
				}
			}
			else
			{
				end();
			}
		}

	}
	static void otp()
	{
		System.out.println("    otp has sent to your registerd mail id	");
			int k = r.nextInt(8999)+1000;
			int otp = display(k);
			check (k);
	}
	static void check(int otp)
	{
		if(otp==sc.nextInt())
		{
			System.out.println("	What do you want change?	");
			String opt=sc.next();
			if(opt.equalsIgnoreCase("id"))
			{
				System.out.println("    enter new userid      ");
				String id = sc.next();
				obj.setuid(id);
				System.out.println("    id updated successfullyy    ");
				System.out.println("	do you want to sigin ");
				sigin();
			}
			else if(opt.equalsIgnoreCase("password"))
			{
				System.out.println("    enter new password      ");
				String pwsd = sc.next();
				obj.setpassword(pwsd);
				System.out.println("    password updated successfullyy    ");
				System.out.println("	do you want to sigin ");
				sigin();
			}
		}
		else
		{
			System.out.print("	you entered wrong otp	");
			System.out.print("	Resend otp	");
			String s=sc.next();
			if(s.equalsIgnoreCase("yes"))
			otp();
			else
			end();
		}
	}
	static void login()
	{	
		System.out.println("       Enter userid and password to create acc");	
		obj = new user();
		System.out.println("       Registraion is successfull  ");
		System.out.println("       do you  want to sigin    ");
		String b = sc.next();
		if(b.equalsIgnoreCase("yes"))
		{
			sigin();
		}
		else
		{
			end();
		}	
	}
	static void start()
	{
       
		System.out.println("	Do you want to start the exam	");
		String s=sc.next();
		if(s.equalsIgnoreCase("yes"))
		{
        		Exam exam = new Exam();
			exam.addQuestion("MS-Word is an example of_____ \n1. An operating system\n2. A processing device\n3. Application software\n4. An input device\n ", 0, 3);
	 	exam.addQuestion("Ctrl, Shift and Alt are called____ keys. \n1. modifier \n2. function \n3. alphanumeric\n4. adjustment\n ",1, 1);
        	exam.addQuestion("National Income estimates in India are prepared by__\n1. Reserve Bank of India\n2. Central statistical organisation\n3.  Planning Commission\n4. Indian statistical Institute\n ",2, 2);
        	exam.addQuestion("Fathometer is used to measure_\n1. Earthquakes\n2. Rainfall\n3. Ocean depth\n4. Sound intensity\n ", 3,3);
       			exam.conductExam();
			end();
		}
		else
		{
			end();
		}
		
	}
	static void end()
	{
                String green="\u001B[32m";
               System.out.print(green);
		System.out.println("		Thank you		");
                String reset="\u001B[0m";
               System.out.print(reset);
               
               
	}
}
class Exam 
{
	private String  questions[];
    	private int answer[];
    	private int userAnswer[];
    	public Exam() 
	{
        	questions = new String[4];
		answer=new int[4];
		userAnswer=new int[4];
    	}
    	public void addQuestion(String question,int qnum,int ans) 
	{
		questions[qnum]=question;
		answer[qnum]=ans; 
    	}
    	public void conductExam() 
	{
        	int score = 0;
        	Scanner sc = new Scanner(System.in);
        	System.out.println("	Your Exam has been Started	");
		int c=0;
        	for (int i = 0; i < questions.length; i++) 
		{		
            		System.out.println("\nQuestion " +( i + 1 )+ ": " + questions[i] );
            		System.out.print("Your answer: ");
           		userAnswer[i] = sc.nextInt();
			if (userAnswer[i]==(answer[i])) 
			{
                		score++;
			}
        	}
        	System.out.println("		Exam finished!		");
		if(score==questions.length)
		{
			String yellow="\u001B[33m";
			String blink="\u001B[5m";
			String reset="\u001B[0m";
			System.out.print(yellow);
			System.out.println(blink);
			System.out.println("		congratulations		");
			System.out.println(reset);
		}
		for(int i=0;i<questions.length;i++)6
		{c
			System.out.println("Q "+(i+1)+" "+" \n actual answer # " +answer[i]+ " \n your Answer #"+ userAnswer[i]);
		}

        		System.out.println("Your score: " + score + " out of " + questions.length);
    	}
}
class Main extends user
{
	public static void main(String[] args) 
	{
                String blue = "\u001B[34m";
                String purple="\u001B[35m";
                String green="\u001B[32m";
                String blink="\u001B[5m";
                String reset="\u001B[0m";
                String yellow="\u001B[33m";
                String red ="\u001B[31m";
                System.out.print(red);
                System.out.println("          ****************************	");
                System.out.print(blue);
                System.out.println(blink);
                System.out.print("            Welcome to the Online Exam!	");
                System.out.println(reset);
                System.out.println(red);
                System.out.print("           ****************************	");
                System.out.println(reset);
		login();
    	}
}
