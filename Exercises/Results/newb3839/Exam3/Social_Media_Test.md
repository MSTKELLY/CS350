using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Social_Media_Newby
{
    //Social_Media - Exam 3
    //Christopher Newby
    //CS 350 - Fall 2017
    //Professor Mark Seaman

    class Person
    {
        //Encapsulate class variables
        private int person_ID { get; set; }
        private string user_name { get; set; }
        private string user_password { get; set; }
        private string first_name { get; set; }
        private string last_name { get; set; }


        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@ API FUNCTION CALLS BELOW THIS LINE @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//

        //Public constructor
        public Person(int p_ID, string p_name, string p_pw, string p_fname, string p_lname)
        {
            person_ID = p_ID;
            user_name = p_name;
            user_password = p_pw;
            first_name = p_fname;
            last_name = p_lname;
        }


        //Get methods for breaking person objects into parts for saving in files
        public int Get_Person_ID()
        {
            return person_ID;
        }
        public string Get_Username()
        {
            return user_name;
        }
        public string Get_PW()
        {
            return user_password;
        }
        public string Get_FN()
        {
            return first_name;
        }
        public string Get_LN()
        {
            return last_name;
        }

        //Login function (EXTRA)
        public bool Person_Login(int login_p_ID, string login_p_pw)
        {
            if (Data_Store.person_list[login_p_ID - 1].user_password.Equals(login_p_pw))
            {
                return true;
            }
            else
            {
                return false;
            }
        }

        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@ API FUNCTION CALLS ABOVE THIS LINE @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//


        //--------------------------------------------------------------------------------------------//
        //--------------------- PRIVATE CLASS FUNCTION CALLS BELOW THIS LINE -------------------------//
        //--------------------------------------------------------------------------------------------//

        //Add person to list
        private void Add_Person_To_List(Person p)
        {
            Data_Store.person_list.Add(p);
        }

        //--------------------------------------------------------------------------------------------//
        //--------------------- PRIVATE CLASS FUNCTION CALLS ABOVE THIS LINE -------------------------//
        //--------------------------------------------------------------------------------------------//
    }
}


using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Social_Media_Newby
{
    class Friend
    {
        //Social_Media - Exam 3
        //Christopher Newby
        //CS 350 - Fall 2017
        //Professor Mark Seaman


        //Encapsulate class variables
        private int person_ID_1 { get; set; }
        private int person_ID_2 { get; set; }


        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@ API FUNCTION CALLS BELOW THIS LINE @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//

        //Public Constructor
        public Friend(int p_ID_1, int p_ID_2)
        {
            //self - friend
            person_ID_1 = p_ID_1;
            person_ID_2 = p_ID_2;
        }

        //Get methods for extracting object information
        public int Get_First_Person()
        {
            return person_ID_1;
        }
        public int Get_Second_Person()
        {
            return person_ID_2;
        }

        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@ API FUNCTION CALLS ABOVE THIS LINE @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//


        //--------------------------------------------------------------------------------------------//
        //--------------------- PRIVATE CLASS FUNCTION CALLS BELOW THIS LINE -------------------------//
        //--------------------------------------------------------------------------------------------//

        //Add/Remove methods
        private void Add_Friend(Friend f)
        {
            Data_Store.friends_list.Add(f);
        }

        private void Remove_Friend(Friend f)
        {
            Data_Store.friends_list.Remove(f);
        }

        //Find person's friends by using their own ID to search for instances of friendships
        private List<Friend> Get_Person_Friend_List(int p_ID)
        {
            List<Friend> temp = new List<Friend>();
            for (int i = 0; i < Data_Store.friends_list.Count; i++)
            {
                if (Data_Store.friends_list[i].person_ID_1 == p_ID || Data_Store.friends_list[i].person_ID_2 == p_ID)
                {
                    temp.Add(Data_Store.friends_list[i]);
                }
            }
            return temp;
        }

        //--------------------------------------------------------------------------------------------//
        //--------------------- PRIVATE CLASS FUNCTION CALLS ABOVE THIS LINE -------------------------//
        //--------------------------------------------------------------------------------------------//
    }
}

using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Social_Media_Newby
{
    //Social_Media - Exam 3
    //Christopher Newby
    //CS 350 - Fall 2017
    //Professor Mark Seaman

    class Post
    {
        //Encapsulate class variables
        private int Post_ID { get; set; }
        private string Post_Topic { get; set; }
        private int Post_Author_ID {get; set;}
        private int Post_ReferredBy_ID { get; set; }
        private string Post_Body { get; set; }


        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@ API FUNCTION CALLS BELOW THIS LINE @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//

        //Public constructor
        public Post(int p_ID, string p_top, int p_auth, int p_refby_ID, string p_body)
        {
            Post_ID = p_ID;
            Post_Topic = p_top;
            Post_Author_ID = p_auth;
            Post_ReferredBy_ID = p_refby_ID;
            Post_Body = p_body;
        }

        //Get methods for retrieving individual object information
        public int Get_Post_ID()
        {
            return Post_ID;
        }

        public string Get_Post_Topic()
        {
            return Post_Topic;
        }

        public int Get_Author_ID()
        {
            return Post_Author_ID;
        }

        public int Get_ReferredBy_ID()
        {
            return Post_ReferredBy_ID;
        }

        public string Get_Post_Body()
        {
            return Post_Body;
        }

        //Search for posts from certain author
        public List<Post> Get_Posts_For_User(int p_ID)
        {
            List<Post> temp = new List<Post>();

            for (int i = 0; i < Data_Store.posts_list.Count; i++)
            {
                if (Data_Store.posts_list[i].Post_Author_ID.Equals(p_ID))
                {
                    temp.Add(Data_Store.post_list_test[i]);
                }
            }
            return temp;
        }

        //Add post to friend by inserting own ID as author
        public void Add_Post_To_Friend(int p_ID, string p_top, int p_auth, int p_refby_ID, string p_bod)
        {
            Post post_from_friend = new Post(p_ID, p_top, p_auth, p_refby_ID, p_bod);

            Data_Store.posts_list.Add(post_from_friend);
        }

        //Remove post from list
        public void Remove_Post(Post p)
        {
            Data_Store.posts_list.Remove(p);
        }

        //Add post to list
        public void Add_Post_To_List(Post p)
        {
            Data_Store.posts_list.Add(p);
        }
        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@ API FUNCTION CALLS ABOVE THIS LINE @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//


        //--------------------------------------------------------------------------------------------//
        //--------------------- PRIVATE CLASS FUNCTION CALLS BELOW THIS LINE -------------------------//
        //--------------------------------------------------------------------------------------------//

        //None needed

        //--------------------------------------------------------------------------------------------//
        //--------------------- PRIVATE CLASS FUNCTION CALLS ABOVE THIS LINE -------------------------//
        //--------------------------------------------------------------------------------------------//
    }
}


using System;
using System.Collections;
using System.Collections.Generic;
using System.Data.SqlClient;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Social_Media_Newby
{
    //Social_Media - Exam 3
    //Christopher Newby
    //CS 350 - Fall 2017
    //Professor Mark Seaman

    class System_Mod
    {
        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@ API FUNCTION CALLS BELOW THIS LINE @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//

        //Clears all data (local & persistent)
        public void Reset_All_Data()
        {
            //Clear local list storage
            Data_Store.person_list.Clear();

            Data_Store.friends_list.Clear();

            Data_Store.posts_list.Clear();

            //Clear local string array test results
            Array.Clear(Data_Store.person_test_results, 0, Data_Store.person_test_results.Length);

            Array.Clear(Data_Store.friend_test_results, 0, Data_Store.friend_test_results.Length);

            Array.Clear(Data_Store.post_test_results, 0, Data_Store.post_test_results.Length);

            //Clear local temporary list storage
            Data_Store.person_list_test.Clear();

            Data_Store.friend_list_test.Clear();

            Data_Store.post_list_test.Clear();

            //GO CLEAR THE DATA FROM FILES HERE
        }

        //Master Import/Export function calls
        public void Export_Data(List<Person> person, List<Friend> friend, List<Post> post)
        {
            string desktop_path = Get_Desktop_Path();

            List<object> result1 = person.Cast<object>().ToList();

            Write_To_CSV(result1, "Person", "Person");

            List<object> result2 = friend.Cast<object>().ToList();

            Write_To_CSV(result2, "Friend", "Friend");

            List<object> result3 = post.Cast<object>().ToList();

            Write_To_CSV(result3, "Post", "Post");
        }

        public void Import_Data()
        {
            Read_From_CSV("Person","Person");

            Read_From_CSV("Friend", "Friend");

            Read_From_CSV("Post", "Post");
        }

        //Gets the path of the desktop for any computer its run on, used for
        public string Get_Desktop_Path()
        {
            return Environment.GetFolderPath(System.Environment.SpecialFolder.DesktopDirectory);
        }

        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@ API FUNCTION CALLS ABOVE THIS LINE @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//


        //--------------------------------------------------------------------------------------------//
        //--------------------- PRIVATE CLASS FUNCTION CALLS BELOW THIS LINE -------------------------//
        //--------------------------------------------------------------------------------------------//

        //Convert from different classes of objects to lines in CSV format
        private string Convert_Person_To_CSV(Person p)
        {
            return (p.Get_Person_ID().ToString() + "," + p.Get_Username() + "," + p.Get_PW() + "," + p.Get_FN() + "," + p.Get_LN());
        }

        private string Convert_Friend_To_CSV(Friend f)
        {
            return (f.Get_First_Person().ToString() + "," + f.Get_Second_Person().ToString());
        }

        private string Convert_Post_To_CSV(Post p)
        {
            return (p.Get_Post_ID().ToString() + "," + p.Get_Post_Topic() + "," + p.Get_Author_ID().ToString() +
                "," + p.Get_ReferredBy_ID().ToString() + "," + p.Get_Post_Body());
        }


        //Convert from lines in CSV file format to different classes of objects
        private Person Convert_CSV_To_Person(string line)
        {
            string[] data = line.Split(',');

            Person new_person = new Person(Convert.ToInt32(data[0]), data[1], data[2], data[3], data[4]);

            return new_person;    
        }

        private Friend Convert_CSV_To_Friend(string line)
        {
            string[] data = line.Split(',');

            Friend new_friend = new Friend(Convert.ToInt32(data[0]), Convert.ToInt32(data[1]));

            return new_friend;
        }

        private Post Convert_CSV_To_Post(string line)
        {
            string[] data = line.Split(',');

            Post new_post = new Post(Convert.ToInt32(data[0]), data[1], Convert.ToInt32(data[2]), Convert.ToInt32(data[3]), data[4]);

            return new_post;
        }


        //Takes in a generic object list, a string saying what type of object should be, and the filename you wish to use for it
        private void Write_To_CSV(List<object> list, string object_type, string file_name)
        {
            try
            {
                string file_path = Get_Desktop_Path() + "\\" + file_name + ".txt";

                string data = "";

                Erase_Data_Files(file_name);

                if (object_type.Equals("Person"))
                {
                    List<Person> result = list.Cast<Person>().ToList();

                    using (System.IO.StreamWriter file = new System.IO.StreamWriter(file_path))
                    {
                        for (int i = 0; i < result.Count; i++)
                        {
                            data = Convert_Person_To_CSV(result[i]);

                            file.WriteLine(data);

                            //data = "";
                        }
                    }
                }
                else if (object_type.Equals("Friend"))
                {
                    List<Friend> result = list.Cast<Friend>().ToList();

                    using (System.IO.StreamWriter file = new System.IO.StreamWriter(file_path))
                    {
                        for (int i = 0; i < result.Count; i++)
                        {
                            data = Convert_Friend_To_CSV(result[i]);

                            file.WriteLine(data);

                            //data = "";
                        }
                    }
                }
                else if (object_type.Equals("Post"))
                {
                    List<Post> result = list.Cast<Post>().ToList();

                    using (System.IO.StreamWriter file = new System.IO.StreamWriter(file_path))
                    {
                        for (int i = 0; i < result.Count; i++)
                        {
                            data = Convert_Post_To_CSV(result[i]);

                            file.WriteLine(data);

                            //data = "";
                        }
                    }
                }
                else
                {
                    Console.WriteLine("Unknown object type detected.");

                    return;
                }
            }
            catch (Exception)
            {
                Console.WriteLine("Something went wrong writing to your CSV file");
            }
        }


        //Read from file and convert the CSV formatted items into their individual object types, and add them to the local lists
        private void Read_From_CSV(string object_type, string file_name)
        {
            try
            {
                string file_path = Get_Desktop_Path() + "\\" + file_name + ".txt";

                List<string> incoming = new List<string>();

                if (object_type.Equals("Person"))
                {
                    using (StreamReader sr = new StreamReader(file_path))
                    {
                        // Read the stream to a string
                        while (!sr.EndOfStream)
                        {
                            string line = sr.ReadLine();

                            incoming.Add(line);
                        }
                    }
                    for(int i = 0; i< incoming.Count; i++)
                    {
                        Person new_person = Convert_CSV_To_Person(incoming[i]);

                        Data_Store.person_list.Add(new_person);
                    }
                }
                else if(object_type.Equals("Friend"))
                {
                    using (StreamReader sr = new StreamReader(file_path))
                    {
                        // Read the stream to a string
                        while (!sr.EndOfStream)
                        {
                            string line = sr.ReadLine();

                            incoming.Add(line);
                        }
                    }
                    for (int i = 0; i < incoming.Count; i++)
                    {
                        Friend new_friend = Convert_CSV_To_Friend(incoming[i]);

                        Data_Store.friends_list.Add(new_friend);
                    }
                }
                else if (object_type.Equals("Post"))
                {
                    using (StreamReader sr = new StreamReader(file_path))
                    {
                        // Read the stream to a string
                        while (!sr.EndOfStream)
                        {
                            string line = sr.ReadLine();

                            incoming.Add(line);
                        }
                    }
                    for (int i = 0; i < incoming.Count; i++)
                    {
                        Post new_post = Convert_CSV_To_Post(incoming[i]);

                        Data_Store.posts_list.Add(new_post);
                    }
                }
                else
                {
                    Console.WriteLine("The CSV you're trying to read is unrecognized.");

                    return;
                }
            }
            catch (Exception)
            {

            }
        }


        //Checks if a file exists, deletes if it exists
        private void Erase_Data_Files(string file_name)
        {
            string file_path = Get_Desktop_Path() + "\\" + file_name + ".txt";

            if (File.Exists(file_path))
            {
                File.Delete(file_path);
            }
        }

        //--------------------------------------------------------------------------------------------//
        //--------------------- PRIVATE CLASS FUNCTION CALLS ABOVE THIS LINE -------------------------//
        //--------------------------------------------------------------------------------------------// 
    }
}


using System;
using System.Collections;
using System.Collections.Generic;
using System.Data;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Data.Sql;

namespace Social_Media_Newby
{
    //Social_Media - Exam 3
    //Christopher Newby
    //CS 350 - Fall 2017
    //Professor Mark Seaman

    class Data_Store
    {
        //Data_Store lists & arrays below are local storage

        //Non-test local storage of persons, friends and posts
        public static List<Person> person_list = new List<Person>();

        public static List<Friend> friends_list = new List<Friend>();

        public static List<Post> posts_list = new List<Post>();


        //Test pass/fail results storage for each module
        public static string[] person_test_results = new string[2];

        public static string[] friend_test_results = new string[3];

        public static string[] post_test_results = new string[3];

        public static string[] system_mod_test_results = new string[3];


        //Temporary test lists
        public static List<Person> person_list_test = new List<Person>();

        public static List<Friend> friend_list_test = new List<Friend>();

        public static List<Post> post_list_test = new List<Post>();
    }
}


using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.IO;

namespace Social_Media_Newby
{
    //*****************************************************************************************************//
    //************************* DEVELOPMENT MOVES AT THE SPEED OF TEST ************************************//
    //*****************************************************************************************************//

    //Social_Media - Exam 3
    //Christopher Newby
    //CS 350 - Fall 2017
    //Professor Mark Seaman

    class Test
    {
        //========================= TEST DATA & LISTS - LOCAL TEST DATA =============================//
        private Person test_person = new Person(1, "Jdoe", "abc123", "John", "Doe");

        private Person test_person1 = new Person(2, "BMan", "123abc", "Barry", "Mannilow");

        private Person test_person2 = new Person(3, "ElRoy", "111abc", "Chuck", "Winslow");

        private Person test_person3 = new Person(4, "BBad", "765qwe", "Javier", "Perez");

        private Friend test_friend = new Friend(2, 1);

        private Friend test_friend1 = new Friend(3, 2);

        private Friend test_friend2 = new Friend(1, 4);

        private Friend test_friend3 = new Friend(4, 3);

        private Post test_post = new Post(1, "ChaCha", 1, 2, "Me likey do da cha cha");

        private Post test_post1 = new Post(2, "ChaCha", 2, 2, "Me likey do da cha cha too");

        private Post test_post2 = new Post(3, "T.P.", 3, 2, "Is 'quilted northern' better than 'cottonelle' toilet paper?");

        private Post test_post3 = new Post(4, "Jello", 4, 4, "Does anyone else hate green jello?!!!");

        private List<Person> person_test_list = new List<Person>();

        private List<Friend> friends_test_list = new List<Friend>();

        private List<Post> posts_test_list = new List<Post>();


        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@ API FUNCTION CALLS BELOW THIS LINE @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//


        //Run master test function call
        public void Run_Master_Test()
        {
            //Execute all test functions
            Person_Registration_Test(1, "abc", "123", "test", "person");

            Person_Login_Test(1, ""); //<---PASS      FAIL ---> //person_login_test(1, "000"); 

            Friend_List_Creation_Test();

            New_Friendship_Test(test_friend);

            Remove_Friendship_Test(test_friend);

            List_All_Posts();

            Add_Topic_From_Friend(test_post);

            Remove_Topic_From_List(test_post);

            Reset_All_Data_Test();

            Export_Data_Test(Data_Store.person_list, Data_Store.friends_list, Data_Store.posts_list);

            Import_Data_Test();
        }

        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@ API FUNCTION CALLS ABOVE THIS LINE @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//
        //@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@//

        //--------------------------------------------------------------------------------------------//
        //--------------------- PRIVATE CLASS FUNCTION CALLS BELOW THIS LINE -------------------------//
        //--------------------------------------------------------------------------------------------//

        //====================== PERSON TEST BLOCK ========================//

        //Tests that a user can register to use the system
        private void Person_Registration_Test(int p_ID, string p_uname, string p_pword, string p_fname, string p_lname)
        {
            try
            {
                Data_Store.person_list.Clear();

                Person new_person = new Person(p_ID, p_uname, p_pword, p_fname, p_lname);

                Data_Store.person_list.Add(new_person);

                Data_Store.person_test_results[0] = "Pass";
            }
            catch (Exception)
            {
                Data_Store.person_test_results[0] = "Fail";

                return;
            }
        }

        //Tests that the user can log in using their person ID and password
        private void Person_Login_Test(int p_ID, string p_pword)
        {
            try
            {
                int pID = Data_Store.person_list[0].Get_Person_ID();

                string pw = Data_Store.person_list[0].Get_PW();

                if (Data_Store.person_list[p_ID-1].Person_Login(p_ID, p_pword))
                {
                    Data_Store.person_test_results[1] = "Pass";
                }
                else
                {
                    Data_Store.person_test_results[1] = "Fail";
                }
            }
            catch (Exception)
            {
                return;
            }
        }

        //====================== FRIEND TEST BLOCK ========================//

        //Tests if you can create a list of 
        private void Friend_List_Creation_Test()
        {
            try
            {
                Data_Store.friends_list.Clear(); //Make sure it's clear first!

                Add_Friend_To_List();

                if (Data_Store.friends_list.Count == 4)
                {
                    Data_Store.friend_test_results[0] = "Pass";
                }
                else
                {
                    Data_Store.friend_test_results[0] = "Fail";
                }
            }
            catch (Exception)
            {
                Data_Store.friend_test_results[0] = "Fail";
                return;
            }

        }

        //Tests if a user can add a new friendship to a list
        private void New_Friendship_Test(Friend new_fship)
        {
            try
            {
                List<Friend> temp = Data_Store.friends_list;

                int preTempCount = temp.Count();

                temp.Add(new_fship);

                int postTempCount = temp.Count();

                if (preTempCount != postTempCount)
                {
                    Data_Store.friend_test_results[1] = "Pass";
                }
                else
                {
                    Data_Store.friend_test_results[1] = "Fail";
                }
            }
            catch (Exception)
            {
                Data_Store.friend_test_results[1] = "Fail";

                return;
            }
        }

        //Tests the removal of a friend object from list
        private void Remove_Friendship_Test(Friend rem_fship)
        {
            try
            {
                List<Friend> temp = Data_Store.friends_list;

                int preListCount = temp.Count();

                temp.Remove(rem_fship);

                int postListCount = temp.Count();

                if (preListCount != postListCount)
                {
                    Data_Store.friend_test_results[2] = "Pass";
                }
                else
                {
                    Data_Store.friend_test_results[2] = "Fail";
                }
            }
            catch (Exception)
            {
                Data_Store.friend_test_results[2] = "Pass";

                return;
            }
        }

        private void List_All_Posts()
        {
            Add_Post_To_List();
            
            List<Post> temp = Data_Store.posts_list;

            if(temp.Count == 4)
            {
                Data_Store.post_test_results[0] = "Pass";
            }
            else
            {
                Data_Store.post_test_results[0] = "Fail";
            }
        }

        private void Add_Topic_From_Friend(Post p)
        {
            Data_Store.posts_list.Clear();

            Data_Store.posts_list.Add(p);

            if (!Data_Store.posts_list[0].Get_Author_ID().Equals(Data_Store.posts_list[0].Get_ReferredBy_ID()))
            {
                Data_Store.post_test_results[1] = "Pass";
            }
            else
            {
                Data_Store.post_test_results[1] = "Fail";
            }
        }

        private void Remove_Topic_From_List(Post p)
        {
            Data_Store.posts_list.Clear();

            int preCount = Data_Store.posts_list.Count();

            Data_Store.posts_list.Add(p);

            int midCount = Data_Store.posts_list.Count();

            Data_Store.posts_list.Remove(p);

            int postCount = Data_Store.posts_list.Count();

            if(preCount == postCount)
            {
                Data_Store.post_test_results[2] = "Pass";
            }
            else
            {
                Data_Store.post_test_results[2] = "Fail";
            }
        }

        private void Reset_All_Data_Test()
        {
            Add_Persons_To_List();

            Add_Friend_To_List();

            Add_Post_To_List();

            int[] beforeCount = new int[3];

            beforeCount[0] = Data_Store.person_list.Count();

            beforeCount[1] = Data_Store.friends_list.Count();

            beforeCount[2] = Data_Store.posts_list.Count();

            System_Mod test = new System_Mod();

            test.Reset_All_Data();

            int[] afterCount = new int[3];

            afterCount[0] = Data_Store.person_list.Count();

            afterCount[1] = Data_Store.friends_list.Count();

            afterCount[2] = Data_Store.posts_list.Count();


            for (int i = 0; i < 3; i++)
            {
                if (beforeCount[i] != afterCount[i])
                {
                    Data_Store.system_mod_test_results[0] = "Pass";
                }
                else
                {
                    Data_Store.system_mod_test_results[0] = "Fail";
                }
            }
        }


        private void Export_Data_Test(List<Person> p_list, List<Friend> f_list, List<Post> pst_list)
        {
            Add_Persons_To_List();

            Add_Friend_To_List();

            Add_Post_To_List();

            List<object> obj = p_list.Cast<object>().ToList();

            System_Mod test = new System_Mod();

            test.Export_Data(p_list, f_list, pst_list);

            string path = test.Get_Desktop_Path() + "\\Person.txt";

            if (File.Exists(path))
            {
                Data_Store.system_mod_test_results[1] = "Pass";
            }
            else
            {
                Data_Store.system_mod_test_results[1] = "Fail";
            }
        }

        private void Import_Data_Test()
        {
            System_Mod test = new System_Mod();

            test.Reset_All_Data();

            test.Import_Data();

            if(Data_Store.posts_list.Count == 4)
            {
                Data_Store.system_mod_test_results[2] = "Pass";
            }
            else
            {
                Data_Store.system_mod_test_results[2] = "Fail";
            }
        }
        //==================== TEST OBJECT LIST LOADING METHODS =======================//
        private void Add_Persons_To_List()
        {
            Data_Store.person_list.Add(test_person);

            Data_Store.person_list.Add(test_person1);

            Data_Store.person_list.Add(test_person2);

            Data_Store.person_list.Add(test_person3);
        }

        private void Add_Friend_To_List()
        {
            Data_Store.friends_list.Add(test_friend);

            Data_Store.friends_list.Add(test_friend1);

            Data_Store.friends_list.Add(test_friend2);

            Data_Store.friends_list.Add(test_friend3);
        }

        private void Add_Post_To_List()
        {
            Data_Store.posts_list.Add(test_post);

            Data_Store.posts_list.Add(test_post1);

            Data_Store.posts_list.Add(test_post2);

            Data_Store.posts_list.Add(test_post3);
        }

        //--------------------------------------------------------------------------------------------//
        //--------------------- PRIVATE CLASS FUNCTION CALLS ABOVE THIS LINE -------------------------//
        //--------------------------------------------------------------------------------------------//
    }
}
